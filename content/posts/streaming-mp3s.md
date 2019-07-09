---
title: 'Streaming MP3''s'
date: Wed, 02 Jun 2004 22:37:46 +0000
draft: false
tags: [Linux]
categories: [Linux]
type: post
---

In April, I was planning to setup an MP3 streaming server on my [Red Hat](http://www.redhat.com) Linux 8 box, [click here](http://jroller.com/page/jmrodri/20040412). I gave up on icecast, since it didn't seem as easy as 1, 2, 3 to install.

Then this month, I was reading my latest [CPU](http://www.computerpoweruser.com/) magazine which contained an article where they went through setting up a media server for your home entertainment system. The article referred to [slimserver 5.1](http://www.slimdevices.com/su_downloads.html) MP3 server from a company called [slimdevices](http://www.slimdevices.com/). The main reason for the server is to stream audio to their squeezebox device. But it works with [XMMS](http://www.xmms.org/), Winamp, and [iTunes](http://www.apple.com/itunes/).

This is a great way to stream your collection of MP3s.

To setup slimserver on Red Hat Linux or [Fedora](http://fedora.redhat.com) Core do the following:

1) download the [RPM](http://www.slimdevices.com/su_downloads.html)  
2) install the RPM, rpm -i slimserver-5.1.5-1.noarch.rpm  
2a) if you're running Red Hat Linux 9 or earlier, you will need to get [perl-Time-HiRes-1.38-3.i386.rpm](http://www.slimdevices.com/downloads/misc/perl-Time-HiRes-1.38-3.i386.rpm)  
3) start up the server, /etc/init.d/slimserver start  
4) point your web browser to http://localhost:9000/ to configure the server.  
5) once configured, point your favorite player to http://localhost:9000/stream.mp3

That's it, I know it isn't 1,2,3, but 5 isn't that bad, you now have a full featured MP3 streamer.