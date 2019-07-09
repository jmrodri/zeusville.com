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