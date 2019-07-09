---
title: 'bash line wrapping problem'
date: Wed, 13 Jun 2007 19:18:50 +0000
draft: false
tags: [Linux, Technology]
categories: [Linux, Technology]
type: post
---

I noticed I was having a line wrapping issue with my bash prompt which really got annoying. It's been at least a month and I finally decided to find a fix for it.

![wrapping problem](http://zeusville.files.wordpress.com/2007/06/wrap.png)

My prompt in .bashrc is `PS1="[\u@\e[0;31m\h\e[1;39m \W]: "`

According to [this post](http://forums.macosxhints.com/archive/index.php/t-17068.html) I need to wrap the escape codes with `\[`. So I changed my prompt to the following and all seems well: `PS1="[\u@\[\e[0;31m\]\h\[\e[1;39m\] \W]: "`

![wrapped fix](http://zeusville.files.wordpress.com/2007/06/wrapfix.png)