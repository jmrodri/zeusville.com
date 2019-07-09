---
title: 'random firefox crashes'
date: Mon, 10 Mar 2008 23:57:24 +0000
draft: false
tags: [Linux]
categories: [Linux]
type: post
---

Liz was trying to work on her myspace page and started getting those wonderful bug buddy dialogs about gecko crashing. It seemed related to flash, because when the video was loading it would crash.

I've seen this happen randomly for me too. It's VERY annoying. So I removed the flash rpm and reinstalled using the tarball. That didn't seem to fix the crash. It was a shot in the dark. Then I found this thread: [Firefox (gecko) Crash on Flash](http://forums.fedoraforum.org/showthread.php?t=171611). I tried one of the other suggestions:

`yum remove alsa-plugins-pulseaudio`

That actually fixed the problem. So she's able to use firefox with myspace again, except now there's no volume control or sound. The soundcard detection plays sound just fine, but gnome-volume-manager pops up a dialog stating there are no gstreamer plugins, though reinstalling alsa-plugins-pulseaudio again doesn't fix it. :( Time for more in depth investigation.
---
### Comments:
#### 
[darrell]( "darrellpf@gmail.com") - <time datetime="2008-03-10 20:46:47">Mar 1, 2008</time>

https://bugzilla.redhat.com/show\_bug.cgi?id=428537
<hr />
#### 
[Dark Falcon]( "spam@choseones.dyndns.org") - <time datetime="2008-03-15 20:47:03">Mar 6, 2008</time>

I had this problem and found that my sound devices in /dev had inappropriate permissions. Sound worked fine logging in as root. I added a couple udev rules to force the correct permissions.
<hr />
