---
title: 'latest modified file using ls'
date: Thu, 06 Aug 2009 13:39:33 +0000
draft: false
tags: [Linux, Technology]
categories: [Linux, Technology]
type: post
---

This morning I wanted to find the latest files I modifed in a directory. My first thought was to use ls -l then pipe that to awk or sort, in short I was going in a very convoluted direction (probably cuz I write Java for a living) :)

My second thought was I bet ls can already get me there. I was close, ls got me most of the way, a pipe to head got me the files/directories I wanted:

```
ls -ct1 | head -10


```
---
### Comments:
####
[Stick](http://www.miscellaneous.net "stick@miscellaneous.net") - <time datetime="2009-08-06 10:35:56">Aug 4, 2009</time>

`ls -ltr` or your more specific evocation: `ls -ct1r -r, --reverse reverse order while sorting`
<hr />
