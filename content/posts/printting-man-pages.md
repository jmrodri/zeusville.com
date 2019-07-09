---
title: 'printting man pages'
date: Thu, 29 Nov 2007 04:04:43 +0000
draft: false
tags: [Linux]
categories: [Linux]
type: post
---

There are times I want to print out a man page or redirect it to a text file for other reasons. Everytime I did `man iptables > iptables.txt` I got a bunch of control characters.

```
IPTABLES(8)                                                        IPTABLES(8)N^HNA^HAM^HME^HE       iptables - administration tool for IPv4 packet filtering and NAT

S^HSY^HYN^HNO^HOP^HPS^HSI^HIS^HS

i^Hip^Hpt^Hta^Hab^Hbl^Hle^Hes^Hs \[^H\[-^H-t^Ht t^Hta^Hab^Hbl^Hle^He\]^H\] -^H-\[^H\[A^HAD^HD\]^H\] chain rule-specification \[options\]

i^Hip^Hpt^Hta^Hab^Hbl^Hle^Hes^Hs \[^H\[-^H-t^Ht t^Hta^Hab^Hbl^Hle^He\]^H\] -^H-I^HI chain \[rulenum\] rule-specification \[options\]

Well there a nice little utility called **col** which filters reverse line feeds from input. Go figure. Here's how to get rid of the noise.

`man iptables | col -b` Which results in

```
IPTABLES(8)                            IPTABLES(8)NAME

       iptables - administration tool for IPv4 packet filtering and NAT

If you redirect the latter to a file, you can print it like any other text file. Enjoy!


```
```
---
### Comments:
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
