---
title: 'desktop effects locks up my box'
date: Wed, 07 Mar 2007 03:11:29 +0000
draft: false
tags: [bling]
categories: [Linux, Technology]
type: post
---

Since I first installed Fedora Core 6, the desktop effects would lock up my box within 30 minutes. The hang requires that I hit the reset button on the box as it doesn't respond to the keyboard or mouse. After reboot, I usually only get about 5 minutes worth of usage before it hangs again. I'm thinking it might be heat related, but I find it odd that turning off desktop effects will yield HOURS of reliable use.

Since I really want the desktop effects to work I restarted my quest again. I installed [beryl](http://www.beryl-project.org/) today to see if that was any better, thinking it might have been something wrong with [compiz](http://www.go-compiz.org/index.php?title=Main_Page). But 30 minutes later, BOOM! It's like clockwork.

I've searching through bug after bug looking for clues:

[http://www.fedoraforum.org/forum/search.php?searchid=3464265](http://www.fedoraforum.org/forum/search.php?searchid=3464265)

[http://www.redhat.com/archives/fedora-package-announce/2007-February/msg00090.html](http://www.redhat.com/archives/fedora-package-announce/2007-February/msg00090.html)

[https://bugs.freedesktop.org/buglist.cgi?query\_format=specific&order=relevance+desc&bug\_status=\_\_all\_\_&product=&content=hang](https://bugs.freedesktop.org/buglist.cgi?query_format=specific&order=relevance+desc&bug_status=__all__&product=&content=hang)

[https://bugs.freedesktop.org/show\_bug.cgi?id=5449](https://bugs.freedesktop.org/show_bug.cgi?id=5449)

[https://bugs.freedesktop.org/show\_bug.cgi?id=5781](https://bugs.freedesktop.org/show_bug.cgi?id=5781)

[https://bugs.freedesktop.org/show\_bug.cgi?id=1280](https://bugs.freedesktop.org/show_bug.cgi?id=1280)

[https://bugs.freedesktop.org/show\_bug.cgi?id=2362](https://bugs.freedesktop.org/show_bug.cgi?id=2362)

[https://bugs.freedesktop.org/show\_bug.cgi?id=5986](https://bugs.freedesktop.org/show_bug.cgi?id=5986)

My hardware:

*   ATI X300 (RV370 \[Radeon X300SE\])

*   AMD Athlon 64 CPU 3200+ (socket 939)

*   1GB CORSAIR memory

*   MSI [K8N Neo-F](http://www.msi.com.tw/program/products/mainboard/mbd/pro_mbd_detail.php?UID=652) (MS-7125)

*   Seagate Barracuda [7200.10](http://www.seagate.com/ww/v/index.jsp?vgnextoid=a62099f4fa74c010VgnVCM100000dd04090aRCRD&locale=en-US) (Perpendicular Recording) 250GB SATA

*   LITE-ON 16x DVD burner

*   Fedora Core 6 x86\_64

The machine is rock solid unless I use desktop effects :(

My plan is as follows:

*   run yum update to make sure I get the latest set of FC6 updates

*   install compiz-debuginfo to see if that offers any more information

*   see if I can ssh into the box when it hangs

*   inspect .xsession-errors (Xorg.0.log doesn't have anything, neither does /var/log/messages)

*   run the opengl screensavers to see if it's a compiz/beryl thing or opengl in general

I'll keep everyone posted on my progress.
---
### Comments:
#### 
[Máirín](http://mihmo.livejournal.com/ "mairin@gmail.com") - <time datetime="2007-03-07 22:05:18">Mar 3, 2007</time>

You should show this to Ajax, I bet he would know what's going on.
<hr />
#### 
[Matt]( "rollingsr@live.com") - <time datetime="2007-03-17 21:57:17">Mar 6, 2007</time>

I am having the exact same problem and so far I have been unsuccessful in finding a solution. I have found that I can SSH into the box and when I issue a TOP command nothing seems abnormal Are you using NetworkManager? I have found that if I repeatedly attempt to connect to various networks I can force the X session to hang. I am unable to issue any commands (mouse still moves though) and I must resort to rebooting the system via the power button. I have a Dell 600m with an x300 card. Have you found a solution?
<hr />
#### 
[Craig]( "squeaky_92@hotmail.com") - <time datetime="2007-03-29 13:02:46">Mar 4, 2007</time>

At least you guys are getting 30 mins i getting the hang within the first 2 mins :s i have a opteron 242 X2 and a 7900gt.
<hr />
#### 
[MattB]( "corvelay@yahoo.com") - <time datetime="2007-04-23 01:48:12">Apr 1, 2007</time>

Well - I did some more searching online and found a message board describing this problem - one of the suggestions was to add a kernel boot up parameter in grub.conf file of "acpi=off". This seems to have worked for me as I have 48 hours uptime since and things are working normally again. Here is a link to the site: http://www.fedoraforum.org/forum/printthread.php?t=139648&pp=80 ACPI is some spec for handling the information a BIOS uses for configuration and power interface(power management). I'm guessing that this is what KDE/X or my graphics card is having trouble with when it freezes/locks/hangs/etc. Hope this helps others out there.
<hr />
#### 
[MattB]( "corvelay@yahoo.com") - <time datetime="2007-04-21 04:29:54">Apr 6, 2007</time>

Is there any update on this? When I first installed FC6 I had this issue - I can't remember what I did to fix it - I've had my machine working normally for a year now and all of a sudden the box locks up or reboots randomly within the first 5-45 mins of use no matter what I try. When the box locks up I can not ssh into it from elsewhere - it's completely frozen. I'm not using 64bit, beryl/compiz or any desktop effects that I know of. I start kde and I think I have to be using at least firefox or another program for this to happen. I have stuff in ~/.xsession-errors but it's DCOP notifications and then X Error: BadMatch, BadPixmap and BadWindow errors that are foreign to me. If anyone has solved this please post! Thanks, Matt.
<hr />
#### 
[Fedora 8 ROCKS! &laquo; zeusville](http://zeusville.wordpress.com/2007/11/08/fedora-8-rocks/ "") - <time datetime="2007-11-08 10:44:57">Nov 4, 2007</time>

\[...\] of X) I should’ve figured as much as my previous attempts resulted in the same behavior: try #1 and try \[...\]
<hr />
