---
title: 'VirtualBox -> KVM'
date: Wed, 13 Oct 2010 21:24:38 +0000
draft: false
tags: [Linux]
---


#### 
[bodhi.zazen](http://bodhizazen.net "bodhizazen@ubuntu.com") - <time datetime="2010-10-13 22:10:15">Oct 3, 2010</time>

Thank you for linking to my blog, glad it helped you.
<hr />
#### 
[bodhi.zazen](http://bodhizazen.net "bodhizazen@ubuntu.com") - <time datetime="2010-11-08 19:13:44">Nov 1, 2010</time>

If you do not mind, here is how to bridge your network card: http://blog.bodhizazen.net/linux/virt-manager-bridged-networking/ I also have a blog on how to "bridge" wireless cards (search my blog if interested, one link is enough here). In terms of KVM vs VBox - It depends on what you want to do exactly. VBox- better for desktops and desktop integration (if you want those things). KVM- better for servers (IMO).
<hr />
#### 
[Andy]( "andy@st-chads.freeserve.co.uk") - <time datetime="2010-10-14 08:52:25">Oct 4, 2010</time>

Can I ask why you moved? Also, if you used the same host, can you tell us about relative performance kvm vs virtualbox? -Andy
<hr />
#### 
[Matt](http://bonecho.wordpress.com/ "matthewgwilkinson@gmail.com") - <time datetime="2010-10-14 10:07:10">Oct 4, 2010</time>

Yeah I would be interested in how VirtualBox stacks up against KVM on Fedora. I am thinking about doing the same, but VirtualBox seems like it has many features and a much more polished GUI, settings, etc. etc.
<hr />
#### 
[David]( "kg4giy@gmail.com") - <time datetime="2010-10-14 11:16:06">Oct 4, 2010</time>

Does this work with that "other" operating system too? I had serious problems installing XP under KVM, so I have to use BOTH on my system and I would like to dump Virtual Box if I can.
<hr />
#### 
[David]( "kg4giy@gmail.com") - <time datetime="2010-10-14 12:09:27">Oct 4, 2010</time>

The short answer is no, BSOD.
<hr />
#### 
[Matt](http://bonecho.wordpress.com/ "matthewgwilkinson@gmail.com") - <time datetime="2010-10-14 13:12:11">Oct 4, 2010</time>

Everything worked for me as you've laid out here, however the deal-breaker came when I realized there was no immediate option to use bridged networking. I use Windows XP as a VM under VirtualBox so that I can use software like VMware vSphere Client and MS Outlook. I can't connect to my domain if I can't use the same subnet as eth0...
<hr />
#### 
[Matt](http://bonecho.wordpress.com/ "matthewgwilkinson@gmail.com") - <time datetime="2010-10-14 13:20:49">Oct 4, 2010</time>

This might work though... http://www.howtoforge.com/virtualization-with-kvm-on-a-fedora-11-server :)
<hr />
