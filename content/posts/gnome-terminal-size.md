---
title: 'Gnome Terminal Size'
date: Mon, 24 Nov 2003 22:45:47 +0000
draft: false
tags: [Linux]
type: post
---

I was trying to figure out how to change the default size of my Gnome Terminal. [![](http://www.jroller.com/resources/jmrodri/gnome-terminal_thumb.png)](http://www.jroller.com/resources/jmrodri/gnome-terminal.png)There isn't any GUI to change this option (been spoiled by Windoze). After doing some [Google](http://www.google.com) searches I found the word I was looking for geometry. Then the ole memory kicked in and I remembered that you can pass in the size to any X Windows application. So I gave it a shot:```
gnome-terminal --geometry 80x60
```VIOLA! Got what I needed.