---
title: 'zmugfs on Fedora 7'
date: Tue, 16 Oct 2007 00:40:55 +0000
draft: false
tags: [zmugfs]
categories: [zmugfs]
type: post
---

I tested out zmugfs on Fedora 7 today and it completely blew up. The objecthook function being passed into simplejson.loads() behaves differently. On Fedora Core 6 (using python 2.4.4 and simplejson 1.3) my objecthook method is called once with the entire JSON response which I can parse and return a Tree object. On Fedora 7 (using python 2.5 and simplejson 1.7) it gets called 152 times with each call being a subset of the original response.

I really would like it to run on Fedora Core 6, but it's pretty dead since Fedora 7 has been out and Fedora 8 will be out soon enough.

So will zeus abandon FC6 support for something new like F7 or F8? Or will zmugfs be updated to work on all Fedora's? Stay tuned for more zmugfs on zeusville. Same zmug channel, same zmug time!

<insert cheezy soap opera music here>
---
### Comments:
####
[Michael DeHaan](http://michaeldehaan.net/ "michael.dehaan@gmail.com") - <time datetime="2007-10-16 08:40:33">Oct 2, 2007</time>

"Same zmug channel, same zmug time!" Jumping jellyfish Batman!
<hr />
####
[zmugfs fixed on Fedora 7 &laquo; zeusville](http://zeusville.wordpress.com/2007/10/16/zmugfs-fixed-on-fedora-7/ "") - <time datetime="2007-10-16 11:24:57">Oct 2, 2007</time>

\[...\] fixed on Fedora 7 16 10 2007 Yesterday I ran into a slight road block with simplejson. But with some playing around in the python \[...\]
<hr />
