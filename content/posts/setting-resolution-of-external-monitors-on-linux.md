---
title: 'Setting resolution of external monitors on Linux'
date: Wed, 04 Mar 2015 20:06:11 +0000
draft: false
tags: [linux, xrandr]
categories: [Linux, Technology]
type: post
---

Connecting my Fedora laptop to an external monitor by default limits the resolution of the external monitor. I know the monitor can do 1920x1080 vs 1024x768. I got tired of looking up the `xrandr` commands so I wrote up a little script.

`Usage: ./addmode x-resolution y-resolution or ./addmode 1920 1080`

If there are multiple monitors it will list them out giving you the option to select the correct one.

**WARNING:** If only one is available it will use that one without prompting. Also the script defaults to 1366x768 unless you pass in an x,y resolution.

```


#!/bin/sh

xres=$1

yres=$2

fullmodeline=$(cvt 1366 768 | grep Modeline | awk '{$1=""; print $0}')

modeline=$(echo $fullmodeline | awk '{print $1}')

monitors=$(xrandr | grep " connected " | awk '{print $1}')

matches=$(echo $monitors | gawk '{print NF}')

case "$matches" in

    0)

       echo "No matches found"

       show=""

       ;;

    1)

       show=$monitors

       ;;

    \*)

       echo

       echo "Multiple matches found..."

       i=1

       for option in $monitors

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

          show=$(echo $monitors | gawk '{print $'$ans'}')

       fi

       ;;

esac

if \[ "" != "$show" \]; then

   #xrandr --newmode $fullmodeline

   xrandr --addmode $show $modeline

fi

You can download the script from [https://gist.github.com/jmrodri/cad187f6cb5d5ed832a3](https://gist.github.com/jmrodri/cad187f6cb5d5ed832a3)


```