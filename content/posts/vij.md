---
title: 'vij'
date: Fri, 10 Oct 2008 21:34:35 +0000
draft: false
tags: [Linux, Technology]
categories: [Linux, Technology]
type: post
---

I've been using a bash function for launching _vim_ for quite a while. I can do things like _vij edit.jsp_ and it would find the edit.jsp and launch vim. The original version looked like this:

```
vij ()

{

find . -name "$1" -exec vim {} \\;

}

The problem would occur when there were more than one file named _edit.jsp_. Running `find . -name edit.jsp` yielded four files:

```
find . -name edit.jsp

./code/webapp/WEB-INF/pages/activationkeys/edit.jsp

./code/webapp/WEB-INF/pages/errata/edit.jsp

./code/webapp/WEB-INF/pages/channel/manage/edit.jsp

./code/webapp/WEB-INF/pages/systems/probes/edit.jsp

_vij_ would exec vim for each of the files found. This is not what I wanted, I only wanted to edit the third one. So with a little hacking I updated it to prompt me if it found more than one, so I could choose the one I wanted.

```
vij edit.jsp

Multiple matches found...

1: ./code/webapp/WEB-INF/pages/activationkeys/edit.jsp

2: ./code/webapp/WEB-INF/pages/errata/edit.jsp

3: ./code/webapp/WEB-INF/pages/kickstart/wizard/profile/advanced/edit.jsp

4: ./code/webapp/WEB-INF/pages/channel/manage/edit.jsp

5: ./code/webapp/WEB-INF/pages/systems/probes/edit.jsp

q: Quit

? 

Simply add this to your $HOME/.bashrc and you'll be all set.

```
vij ()

{

    dafiles=$(find . -type f -name "$1")

    matches=$(echo $dafiles | gawk '{print NF}')

    case "$matches" in

        0)

           echo "No matches found"

           show=""

           ;;

        1)

           show=$dafiles

           ;;

        \*)

           echo

           echo "Multiple matches found..."

           i=1

           for option in $dafiles

           do

              echo "$i: $option"

              i=\`expr $i + 1\`

           done

           echo "q: Quit"

           echo

           read -p "? " ans

           if \[ "q" == "$ans" \]; then

              show=""

           else

              show=$(echo $dafiles | gawk '{print $"'"$ans"'"}')

           fi

           ;;

    esac

    if \[ "" != "$show" \]; then

       vim $show

    fi

}


```
```
```
```