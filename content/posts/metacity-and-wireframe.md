---
title: 'Metacity and Wireframe'
date: Sat, 21 Feb 2004 21:57:38 +0000
draft: false
tags: [Linux]
categories: [Linux]
type: post
---

On my lowly PIII 650Mhz with 512MB ram and an Nvidia GeForce2 MX with 32MB, Metacity and GNOME run slow. Especially when moving windows around, metacity insisted that fullframe window movement was needed. Well, I decided to look on the net again to see if this has changed. And I found the solution [right here](http://wiki.chad.org/wiki.pl?MetacityWireframeDiscussion).
---
### Comments:
#### 
[Jesus M. Rodriguez]( "jmrodri@nc.rr.com") - <time datetime="2004-07-04 22:19:07">Jul 0, 2004</time>

Reminder in case that link dies: Wire frame movements are implemented in metacity! Just run the ?gconf-editor? tool, go to apps/metacity/general, and click on ?reduced\_resources?. Note: I am running GNOME 2.4, as shipped in Fedora Core 1.
<hr />
