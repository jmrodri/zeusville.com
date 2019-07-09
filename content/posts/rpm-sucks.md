---
title: 'RPM sucks'
date: Mon, 23 Feb 2004 15:49:02 +0000
draft: false
tags: [Linux]
categories: [Linux]
type: post
---

[rpm](http://www.rpm.org) is definitely the worst package manager out there. It's way to difficult to use. For instance, given a rpm how do you list the files in it?

I tried

```
rpm --list --file my.rpm
```I simply get the rpm help screen again. Hmmm, I guess it's time to type```
rpm --help
```I search for --list and find that you must specify --query and --package. Ok that makes sense. So I type in```
rpm -qlp my.rpm
```. Ah so package is different than file.
---
### Comments:
####
[Koz](http://www.koziarski.net "michael@koziarski.com") - <time datetime="2004-02-22 19:18:01">Feb 0, 2004</time>

For 'queries' against the rpm database, you need to know the following:


*   if it's a file, use p
*   If it's a package, don't


So if you have bob-2.3.i386.rpm and you want to know what files it includes, you type "rpm -qpl bob-2.3.i386.rpm". Once it installs you only need to say "rpm -ql bob". Not that hard really.
<hr />
####
[Tiaan]( "tiaank@mandleve.com") - <time datetime="2004-02-25 13:43:41">Feb 3, 2004</time>

Why don't you use urpmi? It's a million times better.
<hr />
