---
title: 'desktop effects locks up my box'
date: Wed, 07 Mar 2007 03:11:29 +0000
draft: false
tags: [bling]
categories: [Linux, Technology]
type: post
---

Since I first installed Fedora Core 6, the desktop effects would lock up my box within 30 minutes. The hang requires that I hit the reset button on the box as it doesn't respond to the keyboard or mouse. After reboot, I usually only get about 5 minutes worth of usage before it hangs again. I'm thinking it might be heat related, but I find it odd that turning off desktop effects will yield HOURS of reliable use. Since I really want the desktop effects to work I restarted my quest again. I installed [beryl](http://www.beryl-project.org/) today to see if that was any better, thinking it might have been something wrong with [compiz](http://www.go-compiz.org/index.php?title=Main_Page). But 30 minutes later, BOOM! It's like clockwork. I've searching through bug after bug looking for clues: [http://www.fedoraforum.org/forum/search.php?searchid=3464265](http://www.fedoraforum.org/forum/search.php?searchid=3464265) [http://www.redhat.com/archives/fedora-package-announce/2007-February/msg00090.html](http://www.redhat.com/archives/fedora-package-announce/2007-February/msg00090.html) [https://bugs.freedesktop.org/buglist.cgi?query\_format=specific&order=relevance+desc&bug\_status=\_\_all\_\_&product=&content=hang](https://bugs.freedesktop.org/buglist.cgi?query_format=specific&order=relevance+desc&bug_status=__all__&product=&content=hang) [https://bugs.freedesktop.org/show\_bug.cgi?id=5449](https://bugs.freedesktop.org/show_bug.cgi?id=5449) [https://bugs.freedesktop.org/show\_bug.cgi?id=5781](https://bugs.freedesktop.org/show_bug.cgi?id=5781) [https://bugs.freedesktop.org/show\_bug.cgi?id=1280](https://bugs.freedesktop.org/show_bug.cgi?id=1280) [https://bugs.freedesktop.org/show\_bug.cgi?id=2362](https://bugs.freedesktop.org/show_bug.cgi?id=2362) [https://bugs.freedesktop.org/show\_bug.cgi?id=5986](https://bugs.freedesktop.org/show_bug.cgi?id=5986) My hardware:

*   ATI X300 (RV370 \[Radeon X300SE\])
*   AMD Athlon 64 CPU 3200+ (socket 939)
*   1GB CORSAIR memory
*   MSI [K8N Neo-F](http://www.msi.com.tw/program/products/mainboard/mbd/pro_mbd_detail.php?UID=652) (MS-7125)
*   Seagate Barracuda [7200.10](http://www.seagate.com/ww/v/index.jsp?vgnextoid=a62099f4fa74c010VgnVCM100000dd04090aRCRD&locale=en-US) (Perpendicular Recording) 250GB SATA
*   LITE-ON 16x DVD burner
*   Fedora Core 6 x86\_64

The machine is rock solid unless I use desktop effects :( My plan is as follows:

*   run yum update to make sure I get the latest set of FC6 updates
*   install compiz-debuginfo to see if that offers any more information
*   see if I can ssh into the box when it hangs
*   inspect .xsession-errors (Xorg.0.log doesn't have anything, neither does /var/log/messages)
*   run the opengl screensavers to see if it's a compiz/beryl thing or opengl in general

I'll keep everyone posted on my progress.