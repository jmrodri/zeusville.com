---
title: 'Eclipse Tip: Startup Performance'
date: Wed, 26 May 2004 16:16:03 +0000
draft: false
tags: [Java]
categories: [Java]
type: post
---

I was a bit concerned with [Eclipse's](http://www.eclipse.org) startup performance. It was taking 12 seconds to start up on a machine with dual XEON's a gig of RAM running [Red Hat](http://www.redhat.com) Enterprise Linux ([RHEL](http://www.redhat.com/software/rhel/)). I started digging. I came across a blog which had the following parameters:

\-vmargs -Xverify:none -XX:+UseParallelGC -XX:PermSize=20M  
\-XX:MaxNewSize=32M -XX:NewSize=32M -Xmx160m -Xms160m  

Using these parameters my startup went down to 6 seconds!

Sources:  
[The Blue Pill](http://weblogs.flamefew.net/moatas/archives/000792.html)  
[Running Eclipse](http://download2.eclipse.org/downloads/documentation/2.0/html/plugins/org.eclipse.platform.doc.user/tasks/running_eclipse.htm)