---
title: 'Setting primary display'
date: Mon, 11 Mar 2013 13:55:18 +0000
draft: false
tags: [Linux, Technology]
categories: [Linux, Technology]
type: post
---

When at home I hook up the laptop to an external monitor. For the most part it works great, plug it in and it works. I want the external monitor to be the primary. Pretty simple with `xrandr --output DISPLAY --primary` so I adapted my `[vij](http://zeusville.wordpress.com/2008/10/10/vij/)` command to list out the monitors and present the list to me.```
#!/bin/sh

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
   xrandr --output $show --primary
fi

```When you run the script this is what you see:```
$ bin/prim 

Multiple matches found...
1: LVDS1
2: VGA1
q: Quit

? 

```