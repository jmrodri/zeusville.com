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

* * *

I hate writing HTML pages using HTML.  So I've been in search of a WYSIWYG HTML editor other than

Composer (since I'm using Firefox & Thunderbird).  I like Dreamweaver, I think it's the coolest app out there but I refuse to buy it and run it under emulation.

So searching [Google](http://www.google.com) for [linux html editor](http://www.google.com/search?q=linux+html+editor&sourceid=mozilla-search&start=0&start=0&ie=utf-8&oe=utf-8), I stumbled onto [Nvu](http://www.nvu.com/).

I downloaded the Fedora tarball and gave it a whirl, only to realize the tarball is for Fedora Core 2 Test 1 (I'm running Core 1).  Hmm... so it's time to get dirty and [build it from source](http://www.nvu.com/Building_From_Source.html).  I'm currently in the process of compiling Nvu as I type.  I'll let everyone know how it turns out.  I'm excited to give this a shot.


```
---
### Comments:
#### [turbotad](http://jetteroheller.wordpress.com/ "tadr@scientology.net") - <time datetime="2008-12-28 16:07:07">Dec 0, 2008</time>

Another option you've got is NetBeans. It originally was an IDE for Java, but now edits just about any code that's written using letters and symbols (i.e. just about anything). They added PHP support in the latest version (6.5) and if you edit JSP pages or Velocity or anything from the Java world, there's not much of anything better. It's got especially good Javascript support as well (code completion, etc), has built-in SVN or CVS version control, and for my purposes, generally rocks. Doesn't have very extensive visual editing tools, but they are there. Also, it works on Windows, Mac, Linux or Solaris -- and as I personally run Linux on my primary workstation, have an old Mac PowerBook that I take around when I'm on the go, and have a Windows station I use for A/V work, I like that I can have one IDE I use everywhere. I've done my fair share of ranting about not being able to run Dreamweaver on Linux, but I've found that NetBeans works for the grand majority of the coding work I've got to do on a regular basis.
<hr />
