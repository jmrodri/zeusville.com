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