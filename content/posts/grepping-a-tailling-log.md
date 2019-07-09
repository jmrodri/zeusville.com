---
title: 'grepping a tailling log'
date: Wed, 31 Jan 2007 23:25:39 +0000
draft: false
tags: [Linux, Personal, Technology]
categories: [Linux, Personal, Technology]
type: post
---

`tail -f my.log | grep --line-buffered "what you seek"`
---
### Comments:
#### [Jason Connor](http://glutt.com "jlc@glutt.com") - <time datetime="2007-01-31 20:33:32">Jan 3, 2007</time>

NICE! I was wondering how to do that just a couple of weeks ago. I guess I could have read the entire man page for grep... :-P
<hr />
#### [Stick](http://miscellaneous.net/ "stick@miscellaneous.net") - <time datetime="2007-02-07 18:28:42">Feb 3, 2007</time>

Actually you don't need the line-buffered, by default if stdout is a terminal it is line-buffered.
<hr />
