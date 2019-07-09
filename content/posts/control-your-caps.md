---
title: 'Control your caps'
date: Tue, 16 Aug 2016 18:36:09 +0000
draft: false
tags: [Linux, Technology]
categories: [Linux, Technology]
type: post
---

On all of my computers I use gnome-tweak-tool to remap CAPSLOCK to CTRL. But there are times when I'm working in a virtual machine that doesn't have that setup so I need to go back to old school methods.

If you're on a box just run this from any terminal:

```
setxkbmap -option ctrl:nocaps
```

That avoids trying to kill a program with `C` which usually doesn't work :)
---
### Comments:
#### 
[jmrodri](http://zeusville.wordpress.com/ "jmrodri@gmail.com") - <time datetime="2016-08-16 20:04:02">Aug 2, 2016</time>

that's awesome thanks.
<hr />
#### 
[Daniel Lin](https://plus.google.com/+DanielLin "ephemient@gmail.com") - <time datetime="2016-08-16 19:22:39">Aug 2, 2016</time>

On a distro with systemd, `localectl set-x11-keymap us '' '' ctrl:nocaps` will make that persistent too.
<hr />
#### 
[Links 17/8/2016: GNOME and Debian Anniversaries | Techrights](http://techrights.org/2016/08/17/debian-birthday/ "") - <time datetime="2016-08-17 06:49:52">Aug 3, 2016</time>

\[…\] Control your caps \[…\]
<hr />
