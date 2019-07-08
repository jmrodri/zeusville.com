---
title: 'Note to self'
date: Wed, 03 Sep 2008 01:54:31 +0000
draft: false
tags: [Linux]
type: post
---

I want to run make test-srpm on all of the Makefiles in my tree. Worked great. `find . -name Makefile | sed 's/Makefile//g' |  xargs -n 1 -I foo make -C foo test-srpm` Once I learned sed and awk, combined them with find and xargs, I've gone crazy with the command line. Where once I used to write little Java programs, hrm is that even possible, little Java programs? I now use the command line.