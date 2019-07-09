---
title: 'Computer woes continue'
date: Sat, 03 Jul 2004 22:01:52 +0000
draft: false
tags: [Linux]
categories: [Linux]
type: post
---

On May 30th, I [blogged](http://jroller.com/page/jmrodri/20040530) about my CDRW dying. Turns out it wasn't the culprit of my errors. I had a bad SCSI hard drive which was causing the SCSI bus to freak out and my Tekram 390U2W went south at the same time. The drive finally died, but it stayed alive long enough for me to get my 160 iTunes songs off the drive.

_History_  
Well, the drive dying caused my GRUB to be wiped, I tried reinstalling GRUB on a different drive but never really succeeded. I managed to use the Fedora Rescue CD to mount my Linux partition (which was on a good drive), and tar up my /etc, /opt, and my home directory. My homedir had 1.4GB of stuff email, bookmarks, bunch of RPMs which I installed especially themes. I promptly ftp'd them to my [Red Hat](http://www.redhat.com) 8.0 server. I bought a new [LSI Logic 21040](http://www.newegg.com/app/ViewProductDesc.asp?description=16-118-016&depa=1) U160 SCSI controller. Reinstalled my CDRW, and CDROM (both SCSI).

_Windows Reinstall_  
Now that the hardware was back up and running, I reinstalled [Windows XP Professional](http://www.microsoft.com/windowsxp/pro/default.mspx) and downloaded several megs of updates :) Then I installed [iTunes](http://www.itunes.com) pointed it to the music on a share and fully synced it with my [iPod](http://www.apple.com/ipod/). So Windows was up and running (at least for what I needed it for, using iTunes).

_Linux Reinstall_  
Then today, Saturday, I decided to reinstall [Fedora Core 2](http://fedora.redhat.com). The install took a long time with me watching kids in between screens of the install process. Around 6pm, I had the machine fully installed with Windows on drive 0 and Fedora on drive 1 with GRUB pointing to both.

_Data Restoration_  
Now to restore my data which I so proudly backed up to the server. I open up two gnome-terminals. Ftp to my server and do an

```
mget etc\*.tar opt.tar
```. In the second window, I telnet to my server to see where the hell I put my home directory backup, I thought it was next to the above tar files. Ah, it was except I also gzipped it. I pause to go check on the children. When I come back, in the second window I decide to do a parallel ftp. So I do the following:```
\> ftp corvette
ftp> bin
ftp> prompt
ftp> mget jmrodri.tar.gz
ftp>

```_Royal F\*\*K Up_  
Within seconds I get the ftp prompt back. I was like damn that was a fast transfer. Now this is where frustration, pain, agony, and the expletives kick in. When I realized I had invoked ftp from corvette instead of my freshly installed machine. I ftp'd my homedir tarball on top of itself which promptly made my 1.4GB tarball into a **0** byte file! **!@#$!@@!@#!#@@!**

The lesson learned is I need a better backup process where I can do it at least weekly. So what's the best backup plan for the following setup:

_Plea for help_  
Machine 1: Windows XP Professional - 40GB drive  
Machine 2: Red Hat 8.0 - 100GB drives - runs 24/7  
Machine 3: Windows XP Professional - 18GB SCSI drive / Fedora Core 2 - 18GB SCSI drive (dual boot with GRUB).

Machine 1 and Machine 3 are only on for a few hours at a time. I guess the best thing is to copy important stuff to the share on the server, then put in a backup device on the server which runs on a cron job. Maybe automate my login to always kick off an rsync script to make a backup to the server so it is automatic.

Does anyone have any backup suggestions?

Now I'm going to veg in front of the TV, maybe I'll watch "Gone in Sixty Seconds".