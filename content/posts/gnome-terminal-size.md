---
title: 'Gnome Terminal Size'
date: Mon, 24 Nov 2003 22:45:47 +0000
draft: false
tags: [Linux]
categories: [Linux]
type: post
---

I was trying to figure out how to change the default size of my Gnome Terminal. [![](http://www.jroller.com/resources/jmrodri/gnome-terminal_thumb.png)](http://www.jroller.com/resources/jmrodri/gnome-terminal.png)There isn't any GUI to change this option (been spoiled by Windoze). After doing some [Google](http://www.google.com) searches I found the word I was looking for geometry. Then the ole memory kicked in and I remembered that you can pass in the size to any X Windows application. So I gave it a shot:```
gnome-terminal --geometry 80x60
```VIOLA! Got what I needed.
---
### Comments:
####
[]( "") - <time datetime="2003-11-25 12:24:56">Nov 2, 2003</time>

Gentoo much?
<hr />
####
[Micha]( "mm@wuzup.net") - <time datetime="2007-03-12 17:38:57">Mar 1, 2007</time>

What about a quick 'man gnome-terminal' instead of Google search?
<hr />
####
[me](http://zeusville.wordpress.com "jmrodri@gmail.com") - <time datetime="2007-03-12 22:48:01">Mar 1, 2007</time>

Smart ass comments aren't really required. This post was made in 2003. You can't spread the word of Linux by being a smart ass. Something more like "in the future try man to find out information about a given program" vs your snarky comment.
<hr />
