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