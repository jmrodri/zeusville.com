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