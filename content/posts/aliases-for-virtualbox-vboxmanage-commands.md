---
title: 'aliases for VirtualBox'' VBoxManage commands'
date: Mon, 09 Mar 2015 01:48:55 +0000
draft: false
tags: [linux]
categories: [Linux, Technology]
type: post
---

VBoxManage allows you to interact with VirtualBox using the CLI. You can do just about anything with the command, from starting/stopping VMs. Getting detailed information, modifying or even handling the disks and other storage media. To see all you can do with it checkout this document:

[VBoxManage](https://www.virtualbox.org/manual/ch08.html)

I typically deal with 3 commands, starting/stopping vms and seeing the list of vms.

```


VBoxManage list vms|runningvms|...

VBoxManage startvm vmname --type headless

VBoxManage controlvm vmname savestate|poweroff

To make it easier I created some aliases for the above commands in my .bashrc as bash functions:

*   showvms

*   startvm

*   stopvm

Here are the functions:

```


startvm ()

{

    # start a VM as headless, no need for a GUI

    \_\_davms "startvm" "--type headless"

}

stopvm ()

{

    # allow stopping a VM by saving its state or simply turning it off

    action="savestate"

    if \[ "$1" == "--poweroff" \]; then

       action="poweroff"

    fi

    \_\_davms "controlvm" $action

}

showvms ()

{

    # show all of the VMs including those that are running

    echo "All VMs:"

    VBoxManage list vms

    echo ""

    echo "Runnings VMs:"

    VBoxManage list runningvms

}

All of the bash functions use a common helper function `__davms`. I'm sure there are much nicer ways to alter the list but I stuck with sed and gawk. 

```


\_\_davms ()

{

    cmd="VBoxManage $1"

    # some commands require parameters AFTER the vmname is specified

    cmd\_suffix="$2"

    case "$1" in

        "controlvm")

            davms=$(VBoxManage list runningvms | sed 's/\\"\\ {/\\"-{/' | grep ^\\" | sed 's/\\"//g')

            matches=$(echo $davms | gawk -F '}' '{print NF}')

            ;;

        "startvm")

            davms=$(VBoxManage list vms | sed 's/\\"\\ {/\\"-{/' | grep ^\\" | sed 's/\\"//g')

            matches=$(echo $davms | gawk -F '}' '{print NF}')

            ;;

    esac

    case "$matches" in

        0)

           echo "No vms found"

           show=""

           ;;

        \*)

           echo

           echo "Multiple matches found..."

           i=1

           for option in $davms

           do

              echo "$i: $option" | sed 's/-{/\\ {/'

              i=\`expr $i + 1\`

           done

           echo "q: Quit"

           echo 

           read -p "? " ans

           if \[ "q" == "$ans" \]; then

              show=""

           else

              show=$(echo $davms | gawk '{print $'$ans'}' | sed 's/-{/\\ /' | gawk '{print $1}')

           fi

           ;;

    esac

    if \[ "" != "$show" \]; then

       #$cmd $show $cmd\_suffix

       echo $cmd $show $cmd\_suffix

    fi

}

Here's what you see when you run these commands:

```


$ showvms

All VMs:

"os2" {036ff7c1-81b1-47ee-8c63-af4eff9f8998}

"fedora21" {e43a72c8-ce14-40a4-872a-bc863c186569}

"centos7" {f05e6d7f-b054-4b81-88a0-87f58a9bba53}

"windows7" {d7abca3c-3052-4003-8832-76815fc4d69c}

Runnings VMs:

"windows7" {d7abca3c-3052-4003-8832-76815fc4d69c}

```


$ startvm

Multiple matches found...

1: os2 {036ff7c1-81b1-47ee-8c63-af4eff9f8998}

2: fedora21 {e43a72c8-ce14-40a4-872a-bc863c186569}

3: centos7 {f05e6d7f-b054-4b81-88a0-87f58a9bba53}

4: windows7 {d7abca3c-3052-4003-8832-76815fc4d69c}

q: Quit

? 

```


$ stopvm

Multiple matches found...

1: windows7 {d7abca3c-3052-4003-8832-76815fc4d69c}

q: Quit

? 


```
```
```
```
```
```