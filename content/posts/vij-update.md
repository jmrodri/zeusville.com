---
title: 'vij update'
date: Mon, 06 Feb 2017 15:44:41 +0000
draft: false
tags: [Go, Golang, Java, Linux, Personal, Technology]
categories: [Go, Golang, Java, Linux, Personal, Technology]
type: post
---

[Vij](https://zeusville.wordpress.com/2008/10/10/vij/) is a bash function that makes editing specific files easier to find in a deeply nested directory structure. At the time I was working in [Java](https://www.java.com/en/) which is notorious for having a deep directory structure. In 2008, I updated vij to be more powerful by offering a list of files matching the name, giving you the option to make a choice.

Our current project is in [Golang](https://golang.org/) and I've found a deficiency in vij. We have a vendor directory which contains our dependencies and sometimes vij will find files in the vendor directory which I don't want to edit. It would be nice to exclude a directory from the find command used by vij.

I always want to ignore the vendor directory. But I also want to allow arbitrary names to also be filtered out. The existing vij implementation results in the following crazy output.

```
$ vij util.go

Multiple matches found...

1: ./pkg/broker/util.go

2: ./pkg/fusortest/util.go

3: ./vendor/k8s.io/kubernetes/vendor/golang.org/x/crypto/ssh/terminal/util.go

4: ./vendor/k8s.io/kubernetes/vendor/github.com/vmware/photon-controller-go-sdk/photon/util.go

5: ./vendor/k8s.io/kubernetes/vendor/github.com/spf13/viper/util.go

6: ./vendor/k8s.io/kubernetes/vendor/github.com/spf13/cobra/doc/util.go

...

16: ./vendor/k8s.io/kubernetes/vendor/github.com/kr/pty/util.go

...

108: ./vendor/github.com/coreos/etcd/client/util.go

q: Quit

? 

I just want to see the util.go files in my code tree and ignore all of the ones in vendor. I changed the dafiles variable to have two more options. One is always ignore vendor from the normal use case, but also allow the user to pass in a string to filter on.

```
    if \[ "$3" == "" \]; then

        dafiles=$(find . -type f -name "$2" -not -path "\*/vendor/\*")

    else 

        dafiles=$(find . -type f -name "$2" | grep -v $3)

    fi

Now when I run vij util.go, vij ignores the vendor directory.

```
$ vij util.go

Multiple matches found...

1: ./pkg/broker/util.go

2: ./pkg/fusortest/util.go

q: Quit

? 

Let's say I want to find all files named User\*.java but not the ones in the test directory. You can simply supply "test" as the second argument to vij.

**BEFORE**

```
$ vij User\*.java

Multiple matches found...

1: ./src/main/java/org/candlepin/auth/permissions/UserUserPermission.java

2: ./src/main/java/org/candlepin/auth/permissions/UsernameConsumersPermission.java

3: ./src/main/java/org/candlepin/auth/UserAuth.java

4: ./src/main/java/org/candlepin/auth/UserPrincipal.java

5: ./src/main/java/org/candlepin/model/User.java

6: ./src/main/java/org/candlepin/model/UserCurator.java

7: ./src/main/java/org/candlepin/resource/UserResource.java

8: ./src/main/java/org/candlepin/service/UserServiceAdapter.java

9: ./src/test/java/org/candlepin/auth/UserPrincipalTest.java

10: ./src/test/java/org/candlepin/auth/permissions/UsernameConsumersPermissionTest.java

11: ./src/test/java/org/candlepin/model/UserTest.java

12: ./src/test/java/org/candlepin/resource/UserResourceTest.java

q: Quit

? 

**AFTER**

```
$ vij User\*.java test

Multiple matches found...

1: ./src/main/java/org/candlepin/auth/permissions/UserUserPermission.java

2: ./src/main/java/org/candlepin/auth/permissions/UsernameConsumersPermission.java

3: ./src/main/java/org/candlepin/auth/UserAuth.java

4: ./src/main/java/org/candlepin/auth/UserPrincipal.java

5: ./src/main/java/org/candlepin/model/User.java

6: ./src/main/java/org/candlepin/model/UserCurator.java

7: ./src/main/java/org/candlepin/resource/UserResource.java

8: ./src/main/java/org/candlepin/service/UserServiceAdapter.java

q: Quit

? 

Here's the full implementation of the updated vij:

```
\# reused by other commands that require a filename

\_\_dafiles ()

{

    cmd=$1

    if \[ "$3" == "" \]; then

        dafiles=$(find . -type f -name "$2")

        #dafiles=$(find . -type f -name "$2" -not -path "\*/vendor/\*")

    else

        dafiles=$(find . -type f -name "$2" | grep -v $3)

    fi

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

              show=$(echo $dafiles | gawk '{print $'$ans'}')

           fi

           ;;

    esac

    if \[ "" != "$show" \]; then

       $cmd $show

    fi

}

vij ()

{

    \_\_dafiles "vim" $1 $2

}


```
```
```
```
```
```