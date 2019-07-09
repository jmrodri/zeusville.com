---
title: 'Eclipse you suck!'
date: Thu, 06 Feb 2014 03:18:08 +0000
draft: false
tags: [android]
categories: [Java, Linux, Technology]
type: post
---

I've spent several hours trying to get the Android Developer Toolkit version of eclipse to run on Fedora 20. It's constantly keeps dying with a segfault and libsoup.```
\[13899.331278\] java\[15520\]: segfault at 0 ip 0000003929c70061 sp 00007fb66bd4df40 error 4 in libsoup-2.4.so.1.7.0\[3929c00000+a8000\]

```I've tried all the workarounds on the net which suggest to make it use mozilla, so far no luck.```
\-Dorg.eclipse.swt.browser.DefaultType=mozilla
-Dorg.eclipse.swt.browser.XULRunnerPath=/usr/lib64/xulrunner/

```I even deleted my $HOME/.eclipse, that didn't work. I switched to a new workspace specifically for ADT. Again didn't help, still constantly dies. UGH! Piece of Garbage. And to Ajay, no IntelliJ comments :)