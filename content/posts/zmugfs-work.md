---
title: 'zmugfs work'
date: Wed, 22 Aug 2007 04:34:43 +0000
draft: false
tags: [zmugfs]
categories: [zmugfs]
type: post
---

So I spent the evening trying to figure out how [FUSE](http://fuse.sourceforge.net/) works. I've been looking over the examples: [xmp.py](http://svn.rot13.org/index.cgi/fuse_dbi/view/fuse/cvs/python/xmp.py?rev=4) and [hello.py](http://osdir.com/ml/file-systems.fuse.devel/2006-06/msg00000.html) as well as [gmailfs](http://richard.jones.name/google-hacks/gmail-filesystem/gmail-filesystem.html). I don't have much yet, but it does do "something" :)

After startup:

`[jesusr@camaro src]$ python zmugfs.py -d /tmp/fuse`

`Hey there`

`unique: 1, opcode: INIT (26), nodeid: 0, insize: 56`

`INIT: 7.8`

`flags=0x00000003`

`max_readahead=0x00020000`

`INIT: 7.8`

`flags=0x00000001`

`max_readahead=0x00020000`

`max_write=0x00020000`

`unique: 1, error: 0 (Success), outsize: 40`

`unique: 2, opcode: GETATTR (3), nodeid: 1, insize: 40`

`getattr /`

`unique: 2, error: 0 (Success), outsize: 112`

Doing `[jesusr@camaro ~]$ ls /tmp/fuse/`

`//`

The debug output shows: `unique: 3, opcode: GETATTR (3), nodeid: 1, insize: 40`

`getattr /`

`unique: 3, error: 0 (Success), outsize: 112`

`unique: 4, opcode: GETATTR (3), nodeid: 1, insize: 40`

`getattr /`

`unique: 4, error: 0 (Success), outsize: 112`

`unique: 5, opcode: OPENDIR (27), nodeid: 1, insize: 48`

`unique: 5, error: 0 (Success), outsize: 32`

`unique: 6, opcode: GETATTR (3), nodeid: 1, insize: 40`

`getattr /`

`unique: 6, error: 0 (Success), outsize: 112`

`unique: 7, opcode: READDIR (28), nodeid: 1, insize: 64`

`readdir (/) (0)`

`unique: 7, error: 0 (Success), outsize: 48`

`unique: 8, opcode: READDIR (28), nodeid: 1, insize: 64`

`unique: 8, error: 0 (Success), outsize: 16`

`unique: 9, opcode: RELEASEDIR (29), nodeid: 1, insize: 64`

`unique: 9, error: 0 (Success), outsize: 16`

Now I try `[jesusr@camaro ~]$ mkdir /tmp/fuse/foo`

``mkdir: cannot create directory `/tmp/fuse/foo': File exists``

zmugfs spews out:`unique: 10, opcode: LOOKUP (1), nodeid: 1, insize: 44`

`LOOKUP /foo`

`getattr /foo`

`NODEID: 2`

`unique: 10, error: 0 (Success), outsize: 136`

I know it's not much, but at least I'm seeing what calls need to get implemented. This is going to take a while since this is my first foray into filesystem type stuff and [FUSE](http://fuse.sourceforge.net/).