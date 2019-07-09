---
title: 'WYSIWYG HTML Editor'
date: Wed, 14 Apr 2004 14:10:01 +0000
draft: false
tags: [Linux]
categories: [Linux]
type: post
---

### UPDATE

Nvu built fine, but with lots of debug printing. So I disabled it:

```
./configure --disable-debug
make -f client.mk build\_all

```

* * *

I hate writing HTML pages using HTML. So I've been in search of a WYSIWYG HTML editor other than Composer (since I'm using Firefox & Thunderbird). I like Dreamweaver, I think it's the coolest app out there but I refuse to buy it and run it under emulation.

So searching [Google](http://www.google.com) for [linux html editor](http://www.google.com/search?q=linux+html+editor&sourceid=mozilla-search&start=0&start=0&ie=utf-8&oe=utf-8), I stumbled onto [Nvu](http://www.nvu.com/).

I downloaded the Fedora tarball and gave it a whirl, only to realize the tarball is for Fedora Core 2 Test 1 (I'm running Core 1). Hmm... so it's time to get dirty and [build it from source](http://www.nvu.com/Building_From_Source.html). I'm currently in the process of compiling Nvu as I type. I'll let everyone know how it turns out. I'm excited to give this a shot.