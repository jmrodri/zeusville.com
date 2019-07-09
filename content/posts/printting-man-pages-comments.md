---
title: 'printting man pages'
date: Thu, 29 Nov 2007 04:04:43 +0000
draft: false
tags: [Linux]
categories: [Linux]
type: post
---


#### 
[Robin Norwood]( "robin.norwood@gmail.com") - <time datetime="2007-11-29 00:55:24">Nov 4, 2007</time>

Actually, since the default pager for man is 'less', you can use the less 'save to file' command - 's' - while reading the man page. Also, if you're on the first line of the file, `|$lpr` to pipe everything from the top line to the end to the printer. :-) -RN
<hr />
#### 
[Robin Norwood]( "robin.norwood@gmail.com") - <time datetime="2007-11-29 00:57:37">Nov 4, 2007</time>

Except I just tried that last one, and the formatting is fairly buggered. Oh well.
<hr />
#### 
[Miloslav Trmac](http://carolina.mff.cuni.cz/~trmac/blog/ "mitr@volny.cz") - <time datetime="2007-11-29 06:59:08">Nov 4, 2007</time>

If you want to print a man page, you can also use

> man -t iptables

which directly generates PostScript.
<hr />
