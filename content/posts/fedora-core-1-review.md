---
title: 'Fedora Core 1 Review'
date: Fri, 07 Nov 2003 20:04:20 +0000
draft: false
tags: [Linux]
categories: [Linux]
type: post
---

_Installation_
The installation was fairly uneventful. This was a clean install to an 18.4GB SCSI drive. The drive previously had a Windows partition which I used Disk Druid to delete and repartition for LInux. This was probably the only snafu I hit because I kept getting an error, but it was just user error. After the third try I got the partitions straightened out.

The biggest mistake I made was placing GRUB on the master boot record (MBR) instead of on /dev/sdb1, since it wiped out my current install of AiRBoot and OS boot loaded that works great with OS/2.

_First Reboot_
Upon reboot I expected problems, just being pessimistic I guess, but the reboot went great. I was surprised by a wonderful graphical boot screen which is nice and simple. I love the show/hide detail button since I like to see what's going on during booting especially the first time.

I ran into only one problem where smartd failed to start. I don't much care since I have no idea what this is for :) yet.

_Welcome Screen_
The to be expected Welcome Screen appeared and the user setup was flawless and simple. Nice touch.

_Hardware detection_
This impressed me the most since Fedora found all of my hardware, though I really don't have anything that's rare since my system used to run OS/2 Warp 4 which is extremely picky with hardware.

_Printer horrors_
Now I continue to struggle with the printer on Linux. I have a Canon S750 which is shared via Samba from another Linux (Red Hat 8). I installed the [Turbo Print](http://www.turboprint.de/english.html) driver for it on that machine. So Windows prints just fine to the raw queue, but I don't get all the nice feature on my Fedora install unless I purchase a driver for it. I found the S600 driver works, but it's not the same. So if I were rating Fedora on printer drivers, I'd give it a 4 out of 10.

_Summary_ All in all. I found Fedora much more polished than Red Hat Linux 9. I'm going to try a Personal Desktop install on my other drive just to see how that installation goes. But I think I'll leave Windows again and hang out with Fedora for a while.
---
### Comments:
####
[]( "") - <time datetime="2003-11-08 01:28:02">Nov 6, 2003</time>

smartd is for hard drives that have that S.M.A.R.T. support (to tell you when they think you should buy a new one :-)
<hr />
