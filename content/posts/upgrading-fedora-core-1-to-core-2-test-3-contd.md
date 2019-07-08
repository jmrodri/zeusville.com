---
title: 'Upgrading Fedora Core 1 to Core 2 test 3 (cont''d)'
date: Mon, 17 May 2004 22:09:36 +0000
draft: false
tags: [Linux]
type: post
---

I had blogged on 5/14 that I was going to upgrade to Core 2 this weekend. Well, I actually upgraded that night. I just got the fever to upgrade. So two hours later (5/13 12:30AM), I got [Fedora](http://fedora.redhat.com) Core 2 Test 3 installed (actually upgraded).

After burning the four ISOs, I inserted disc 1 while still logged on to the system. Fedora auto mounted the drive and prompted me to run the autorun script. I answered yes, and the installer proceeded to list the package it was going to update. I'm not that trusting, so I quit up2date, and rebooted. Though that was nice feature and when GA Core 2 comes out this week, I will probably go that route.

I rebooted using disc 1, not to make the same mistake I made with Test 2, I tested all four discs to avoid any surprises. All the discs checked out and I proceeded to install. The first screen asked whether I wanted to upgrade the current install or install new. I chose to upgrade (this option wasn't present in test 2). Then I was asked if I wanted to update my [GRUB](http://www.gnu.org/software/grub/) configuration, to which I answered yes.

A dialog appears stating I need all four CDs, personally this should've been done before it asked me to update my GRUB setup. Nothing should happen to my system until it has decided I have everything I needed.

It's now 11:06PM, I click continue to resume the installation resulting in a "Preparing RPM transaction, the Preparing to install" dialogs. The installer states 45 minutes remain (we'll see to that).

Meanwhile, I decide to read the Release Notes. After 6 minutes, the installer states I have 50 minutes (now it's 11:22PM). I'm prompted to insert disc 2, then disc 3 is inserted at 11:55PM with only 10 minutes to go. Th installer some how caught up, by 12:01AM, I am prompted to reboot.

This is where the fun begins. I reboot the machine knowing I won't see the graphical boot because of the [NVIDIA](http://www.nvidia.com/object/linux_display_ia32_1.0-5336.html) driver I had installed.

Every time I upgrade the kernel, I have to rebuild the stupid driver. This is where Windoze is much better than Linux. I shouldn't have to rebuild my drivers when I upgrade the kernel, I understand why technically it must be done. But a user shouldn't have to worry about this. They just want the machine to automagically work, especially during an upgrade. I would've preferred that the installer stated, "You are running the NVIDIA proprietary driver, in order to guarantee stability, we will use the supplied NVIDIA driver". This way the graphical boot would've worked immediately upon reboot, allowing the user to reinstall the proprietary driver later (if needed at all).

After attempting to reinstall the NVIDIA driver (which didn't work with the 2.6 kernel, I reverted to the supplied nv driver). This is totally NVIDIA's fault, not [Fedora](http://fedora.redhat.com)'s. So don't count this against the Fedora.

Once I fixed the driver issue and rebooted, the graphical boot appeared. Then two other drivers failed, the twoos2two virtual machine driver failed, as did my cisco vpnclient driver, both of which need to be recompiled for the new 2.6 kernel. Again, this shouldn't have to be done.

I got to the login screen, bear in mind that my custom GDM theme was replaced by the default Fedora Core 2 theme which was a bit annoying for an "upgrade". I logged in, whew my users are still defined :) All of my themes are still there so at least that wasn't messed with. But a dialog appeared with the error "XKB config error". So a quick [Google](http://www.google.com) search for ["XKB config error"](http://www.google.com/search?hl=en&lr=&ie=UTF-8&q=xkb+config+error&btnG=Search) I had to replace "xfree86" with "xorg" in my /etc/X11/XF86Config file. NOTE: removing the line didn't help as stated in on of the posts. Another reboot, and viola. I'm running Fedora Core 2 Test 3.

The upgrade when far smoother than I anticipated. The three driver problems I anticipated since I've had them before after updating my kernel in Core 1. The XKB was new, but simple to fix.