---
title: 'Note to self'
date: Mon, 10 Aug 2009 19:43:35 +0000
draft: false
tags: [Linux]
categories: [Linux]
type: post
---

Making the following changes to /etc/pulse/default.pa seems to fix the hanging audio of the flash-plugin and banshee:

`load-module module-hal-detect **tsched=0**`

For more information click here: [https://fedoraproject.org/wiki/Features/GlitchFreeAudio](https://fedoraproject.org/wiki/Features/GlitchFreeAudio)
---
### Comments:
#### 
[Livio](http://blog.jakubrusinek.pl/ "jakub.rusinek@gmail.com") - <time datetime="2009-08-10 16:19:54">Aug 1, 2009</time>

Depends on hardware. On some configs tsched=0 can make PA even more crashy.
<hr />
#### 
[Adam Williamson](http://www.happyassassin.net "adamwill@shaw.ca") - <time datetime="2009-08-10 20:10:44">Aug 1, 2009</time>

When this 'fixes' things for you, it means your sound driver (at the kernel level) is buggy, and you ought to file a bug. We want to have all remaining cases of this problem fixed. Thanks.
<hr />
