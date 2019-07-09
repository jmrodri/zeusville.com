---
title: 'desktop effects locks up my box (part 2)'
date: Wed, 07 Mar 2007 04:34:24 +0000
draft: false
tags: [bling]
categories: [Linux, Personal, Technology]
type: post
---

The [list of packages](http://zeusville.wordpress.com/packages-20070306/) installed on my machine valid as of March 06, 2007 at 11:18pm.

The .xsession-errors file shows some interesting bits:

```


(process:2789): GLib-WARNING \*\*: GError set over the top of a previous GError or uninitialized memory.

This indicates a bug in someone's code. You must ensure an error is NULL before it's set.

The overwriting error message was: File not found

compiz: Failed to load slide: fedora-logo

(process:2789): GLib-WARNING \*\*: GError set over the top of a previous GError or uninitialized memory.

This indicates a bug in someone's code. You must ensure an error is NULL before it's set.

The overwriting error message was: File not found

compiz: Failed to load slide: /usr/share/pixmaps/fedora-logo

compiz: water: GL\_ARB\_fragment\_program is missing

At the time of the hang I was running (from the UI perspective):

*   firefox

*   bouncingcows

*   eclipse

*   gnome-terminal

I was able to ssh into the box after the hang.  `top` showed the following bit of info:

```


VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND

469m  111m 17m R 99.4 11.1   6:25.66 Xorg

while `strace` dumped out the following message 1021 times before I killed it:

```


--- SIGALRM (Alarm clock) @ 0 (0) ---

rt\_sigreturn(0xe)                       = -1 EBUSY (Device or resource busy)

ioctl(7, 0x6444, 0)                     = -1 EBUSY (Device or resource busy)

--- SIGALRM (Alarm clock) @ 0 (0) ---

rt\_sigreturn(0xe)                       = -1 EBUSY (Device or resource busy)

ioctl(7, 0x6444, 0)                     = -1 EBUSY (Device or resource busy)

ioctl(7, 0x6444, 0)                     = -1 EBUSY (Device or resource busy)

--- SIGALRM (Alarm clock) @ 0 (0) ---

rt\_sigreturn(0xe)                       = -1 EBUSY (Device or resource busy)

ioctl(7, 0x6444, 0)                     = -1 EBUSY (Device or resource busy)

ioctl(7, 0x6444, 0)                     = -1 EBUSY (Device or resource busy)


```
```
```
---
### Comments:
#### [Jason Connor](http://glutt.com "jlc@glutt.com") - <time datetime="2007-03-08 14:02:09">Mar 4, 2007</time>

Hi Jesus, You know, I had the same trouble on my laptop, which also has an ATI video card. However, I didn't ever get it to lock up on my desktop machine, which has an NVidia card and I've got the proprietary driver installed. I suspect the driver. I haven't, yet, tried the proprietary ATI driver (if there is one).
<hr />
#### [Daniele Masini](http://vandali.org/DanieleMasini "d.masini@tiscali.it") - <time datetime="2007-03-14 05:28:13">Mar 3, 2007</time>

I have the same problem (since some time ago) with two PCs: one with a nVidia card and the other with an ATI card. When I installed FC6, compiz worked well (on each of my PCs). But some time ago I noticed that the upper face of the cube was empty (no image) and no image even displayed for the skydome. The error reported in my .xsession-errors file is the same you have reported. I tried to specify other png files but the problem persist. I tried with a svg file and the image was shown in the cube upper face but not in the skydome. Have you any idea/solution about that?
<hr />
