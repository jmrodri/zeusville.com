---
title: 'bash line wrapping problem'
date: Wed, 13 Jun 2007 19:18:50 +0000
draft: false
tags: [Linux, Technology]
---


#### 
[momo]( "nbeyhurst@gmail.com") - <time datetime="2007-10-30 11:51:51">Oct 2, 2007</time>

works! ty :)
<hr />
#### 
[Nassty](http://geek-o-matic.com.ar "nassty@nassty.com.ar") - <time datetime="2008-04-27 03:04:16">Apr 0, 2008</time>

worked for me too Thanks!
<hr />
#### 
[Dongsheng Cai](http://log.dongsheng.org "imdongsheng@gmail.com") - <time datetime="2010-04-29 04:42:29">Apr 4, 2010</time>

Thanks! Finally found the workaround for this problem :-)
<hr />
#### 
[serenity]( "serenity@exscape.org") - <time datetime="2009-01-31 12:13:23">Jan 6, 2009</time>

THANK YOU! This has been driving me mad!
<hr />
#### 
[martin](http://digi.ch "blogs@digi.ch") - <time datetime="2009-04-06 17:36:20">Apr 1, 2009</time>

Thank you, you made my life much easier. Maybe you could add some explenations on your other bash options too, seem to do a nice job, it would just be nice to know what they exactly mean, without rtfm. :)
<hr />
#### 
[Shai&#039;s technical blog &raquo; Blog Archive &raquo; bash line wrapping problem](http://wp.shaibn.com/bash-line-wrapping-problem "") - <time datetime="2011-07-14 08:58:18">Jul 4, 2011</time>

\[...\] http://zeusville.wordpress.com/2007/06/13/bash-line-wrapping-problem/ \[...\]
<hr />
#### 
[markfaine](http://twitter.com/markfaine "markfaine@twitter.example.com") - <time datetime="2011-06-17 10:41:09">Jun 5, 2011</time>

This works okay but what about when you want to echo output such as $ echo -e '\\\[\\e\[0;32m\\\]' This is green You get: \\\[\\\] This is green The escaped \[ characters are printed.
<hr />
#### 
[Greg]( "gdwarner@gmail.com") - <time datetime="2011-04-28 14:02:27">Apr 4, 2011</time>

I just added the following to my .bashrc. No need to mess with the PS1. export TERM=linux
<hr />
#### 
[Command Prompt colors](http://www.linuxquestions.org/questions/linux-enterprise-47/command-prompt-colors-936765/#post4638174 "") - <time datetime="2012-03-27 19:44:19">Mar 2, 2012</time>

\[...\] This results in the following value for PS1: '\[e\[0;34m\]h:w \[!\]$\[e\[m\] ' then here and here I hope it \[...\]
<hr />
#### 
[jmrodri](http://zeusville.wordpress.com/ "jmrodri@gmail.com") - <time datetime="2011-06-15 22:40:44">Jun 3, 2011</time>

Glad you found it useful.
<hr />
#### 
[maximilianh](http://twitter.com/maximilianh "maximilianh@twitter.example.com") - <time datetime="2011-06-15 14:46:15">Jun 3, 2011</time>

Thanks for both remarks. export TERM=linux and the nice PS1 works well, but I started to like my new colorful PS1
<hr />
#### 
[diagonaldevice]( "diagonaldevice@gmail.com") - <time datetime="2011-07-07 15:45:37">Jul 4, 2011</time>

Thanks. I made the same exact mistake you did. A long time ago I made a custom bash prompt on Linux, and when I installed MSYS on Windows, I figured I would quickly throw a prompt together based on what I could remember (which apparently wasn't enough). Interestingly, the problem doesn't occur if bash is run from Windows' own cmd (possibly because cmd isn't a proper tty emulator?). Also, congrats for the high-ranking page on Google!
<hr />
#### 
[(problem) Linux command line overwrites itself on long commands.](http://www.linuxquestions.org/questions/linux-newbie-8/problem-linux-command-line-overwrites-itself-on-long-commands-914127/#post4527701 "") - <time datetime="2011-11-18 14:33:09">Nov 5, 2011</time>

\[...\] PS1='\[e\[0;31m\]t\[e\[m\]-\[e\[0;32m\]u\[e\[m\]@\[e\[0;36m\]h\[e\[m\]:\[e\[0;23m\]w\[e\[me\[0;32m\]$\[e\[m\]' See "3.4 Non-Printing Characters in Prompts": http://www.linuxselfhelp.com/howtos/...t-HOWTO-3.html Also: http://zeusville.wordpress.com/2007/...pping-problem/ \[...\]
<hr />
#### 
[Leho Kraav (@lkraav)](http://twitter.com/lkraav "lkraav@twitter.example.com") - <time datetime="2011-11-20 10:41:08">Nov 0, 2011</time>

another happy colorful bash prompt camper here now :>
<hr />
#### 
[kev]( "passby@hotmail.com") - <time datetime="2012-11-18 12:17:33">Nov 0, 2012</time>

Just want you know someone still finds it useful after 5 years. Thank you very much!
<hr />
#### 
[skelly1983](http://www.comptecsystems.co "cipher_no1@hotmail.com") - <time datetime="2013-04-18 15:52:43">Apr 4, 2013</time>

been trying to sort this wrapping problem for hours, thank you worked just fine
<hr />
