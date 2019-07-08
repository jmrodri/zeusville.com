---
title: 'Sony Clie & Linux (Fedora and Red Hat Enterprise Linux)'
date: Wed, 26 May 2004 10:32:32 +0000
draft: false
tags: [Linux]
type: post
---

I've been having fun with my Sony [Clié](http://jroller.com/page/jmrodri/20040524). Unfortunately, I could not connect to [Red Hat Enterprise Linux (RHEL)](http://www.redhat.com/software/rhel/) using pilot-xfer via USB. I kept getting "no suitable driver" error. Determined to sync my new Clié, when I got home, I booted up my crusty [Windows XP](http://www.microsoft.com/windowsxp/default.asp) partition. Installed the Sony Clié software. I did a Hotsync, and installed two trial games. Worked great. Say what you will about Windows, it definitely has a leg up on Linux. Now that I've successfully synced my PDA, I decided to boot [Fedora Core 2](http://fedora.redhat.com) to try my luck. Hopefully, I fair better than I did with RHEL 3. ![](http://jroller.com/resources/jmrodri/gnome-pilot.png) I tried using [gnome-pilot](http://www.gnome.org/projects/gnome-pilot/), filled in /dev/pilot as the port, and click on USB. I then click the Forward button, and chose "Yes, I've used sync software with this pilot before.", and clicked Forward again. I pressed the Hotsync button on my PDA, and gnome-pilot sits there. No activity. I waited until the Sony timed out. ![](http://jroller.com/resources/jmrodri/gnome-pilot2.png) So I remember reading somewhere that if gnome-pilot doesn't work use [pilot-xfer](http://www.tldp.org/HOWTO/PalmOS-HOWTO/pilotlink.html). As me (not root), I try```
pilot-xfer -l
```. Hmm. so /dev/pilot doesn't exist. I remember that I didn't run /sbin/modprobe (from my experience with RHEL). So I su to root, run```
/sbin/modprobe visor
```Then I look at /var/log/messages and notice the following message:```
May 25 22:48:38 firebird kernel: usb 1-2: Handspring Visor /
Palm OS converter now attached to ttyUSB0
(or usb/tts/0 for devfs)
```Lightbulb! Ok I run```
pilot-xfer -p /dev/ttyUSB0 -l
```as me again. Tells me I need to chmod 0666 /dev/ttyUSB0. ARGH! I become root and do as stated. Now as me again, I re-run pilot-xfer. BINGO! Success! I get back the list of items on my Sony Clié. So I take it a step further,```
pilot-xfer -p /dev/ttyUSB0 -backup /home/jmrodri/palm
```and I have 75 file files (.prc & .pdb). Now we're rockin' and rollin'. ![](http://jroller.com/resources/jmrodri/pilot-xfer.png) WHEW! That was tiring. Ok let's see if we can get gnome-pilot to work now that we know to use /dev/ttyUSB0. And again, it sits there. So I'm going to guess that gnome-pilot sucks :) At least pilot-xfer works. I'll keep toying around with it until I'm satisfied. In general Linux has potential, but it is still years behind Windows in usability. The fact that I had to deal with the /dev file system (which a normal user should not have to worry about) and use a command line application to sync my PDA, is beyond a regular desktop user. Hopefully, [Red Hat Desktop](http://www.redhat.com/software/rhel/desktop/) has the ability to sync with PDAs, and other consumer (and business) devices, if it hopes to unseat Windows in the enterprise.