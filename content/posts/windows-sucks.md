---
title: 'WINDOWS SUCKS!'
date: Sun, 28 Jan 2007 23:35:39 +0000
draft: false
tags: [Linux, Technology]
categories: [Linux, Technology]
type: post
---

My in-laws dropped off two computers for me to "debug". A Pentium 4 based desktop with Windows XP. Main problem was internet access. Turns out there was no network config. Windows can't seem to see the network card, and can't load the drivers. I download the latest drivers for the motherboard including a new BIOS. I flash the BIOS, and the machine boots but Windows doesn't. It just hangs. Booting into "Safe Mode" causes it to hang with ...Mup.sys. Still don't know what is going on. The problem is obviously common: [annoyances](http://www.annoyances.org/exec/forum/winxp/1169539430).

The other machine is a Dell laptop, that boots fine until you login. Then it shows the start menu panel,

and the busy cursor. It waits, and waits, and waits. Then it shows up. The complaint? "computer is slow and lot's of errors". I see in the Event Viewer there are several "Application Errors", but the dialog shows "component unknown", gee great help you are. ARGH! I also saw that WIA (Windows Image Acquisition) service won't start. Debugging a service in Windows is nothing short of voodoo. I mean, in Linux I can start the application from the command line and see the errors. In Windows, there's got to be some registry hack that will either turn up the debug level of the service or completely hose the damn machine.

I have to say WINDOWS SUCKS! I hate having to deal with these freaking machines. But I can't in good conscience let my in-laws go to Best Buy to have it worked on. I think it's just silly to pay for "computer service". I've toyed with the idea of switching them to Linux, but I'm worried that I might create a different set of support calls.
---
### Comments:
####
[jmrodri](http://zeusville.wordpress.com/ "jmrodri@gmail.com") - <time datetime="2007-01-28 20:09:08">Jan 0, 2007</time>

Resetting the BIOS to default values seemed to fix the mup.sys error during boots. This is odd since I just finished flashing the BIOS. Oh well. On to the next problem.
<hr />
####
[James Bowes](http://jbowes.dangerouslyinc.com "jbowes@gmail.com") - <time datetime="2007-01-28 20:58:00">Jan 0, 2007</time>

50 bucks says you'll have to reinstall.
<hr />
####
[Máirín](http://mihmo.livejournal.com "mairin@gmail.com") - <time datetime="2007-01-28 21:33:51">Jan 0, 2007</time>

At least if you put them on Linux, you could ssh to fix the problem (given no network issues of course.) For what they use the computer for is it feasible? You could always do a trial run using the FC6 live CD...
<hr />
####
[Jason Connor](http://glutt.com "jlc@glutt.com") - <time datetime="2007-01-29 01:43:19">Jan 1, 2007</time>

Windows Sucks ... Amen
<hr />
####
[Todd](http://www.dma.org/cgi-bin/cgiwrap/tw/toddblog "taw@pobox.com") - <time datetime="2007-01-31 09:30:33">Jan 3, 2007</time>

I have been extremely reluctant to move people to Linux. I just don't want to help them over the learning curve. With windows I just tell them to "go away" since I haven't played with windows in over 10 years now. :) You could convince them to \*buy\* RHEL so that you put the burden on Red Hat's support system. :) -todd
<hr />
