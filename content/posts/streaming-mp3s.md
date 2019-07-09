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
---
### Comments:
#### 
[Laust M. Ladefoged](http://www.defoged.dk "") - <time datetime="2004-06-03 05:21:55">Jun 4, 2004</time>

I have been using the [StreamSicle](http://streamsicle.com) project with great joy for the same type of functionality.

It is a Java web application and songs is selected via browser interface.

Works very nicely and is open source so you can make it fit your needs.

I just checked and the development seems to be at a halt for the last year or so, but the product as is working with no problems for me.
<hr />
#### 
[Jesus M. Rodriguez](http://www.jroller.com/page/jmrodri "jmrodri@nc.rr.com") - <time datetime="2004-06-03 09:40:33">Jun 4, 2004</time>

Looks good. I'm downloading it now. Since I'm a Java developer, I'd love to have something to tweak. Thanks for the comment.
<hr />
#### 
[Partha]( "") - <time datetime="2004-06-03 10:24:30">Jun 4, 2004</time>

You can always try net juke.. Seems to be an application that does exactly what you want http://www.netjuke.org/
<hr />
#### 
[Kev Spencer](http://vek.perlmonk.org "vek@perlmonk.org") - <time datetime="2004-06-03 14:46:27">Jun 4, 2004</time>

I know you're a Java guy but if you ever want to dabble in Apache/mod\_perl then take a peek at [Apache::MP3](http://search.cpan.org/~lds/Apache-MP3-3.05/MP3.pm).
<hr />
