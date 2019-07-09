---
title: 'getting a specific line from a live log file'
date: Wed, 24 Jan 2007 17:15:01 +0000
draft: false
tags: [Linux, Technology]
categories: [Linux, Technology]
type: post
---

Here's how you can find all lines with call\_function in a log file that you are tailing.

```


tail -f catalina.out | grep --line-buffered call\_function


```