---
title: 'desktop effects locks up my box'
date: Wed, 07 Mar 2007 03:11:29 +0000
draft: false
tags: [bling, Linux, Technology]
---


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
