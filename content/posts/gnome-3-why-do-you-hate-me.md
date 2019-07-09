---
title: 'Gnome 3 why do you hate me?'
date: Mon, 04 Mar 2013 14:58:14 +0000
draft: false
tags: [Linux, Technology]
categories: [Linux, Technology]
type: post
---

So my Gnome 3 (gnome-shell, Fedora 18) went to screensaver. When I unlocked it this is what my desktop looks like.

[![lockup](http://zeusville.files.wordpress.com/2013/03/lockup.png?w=549)](http://zeusville.files.wordpress.com/2013/03/lockup.png)

How do I get out of this? My machine is running fine. I can ssh into it and it's running normal but I can't interact with the desktop. Quite annoying.
---
### Comments:
####
[jmrodri](http://zeusville.wordpress.com/ "jmrodri@gmail.com") - <time datetime="2013-03-04 11:02:08">Mar 1, 2013</time>

The answer was ALT-F2 r to restart gnome-shell. :(
<hr />
####
[Bruno Rodrigues]( "shotsbros@hotmail.com") - <time datetime="2013-03-04 11:22:28">Mar 1, 2013</time>

CTRL + ALT + F2 Login in and kill the gnome-shell pid
<hr />
####
[Máirín Duffy](http://blog.linuxgrrl.com "duffy@fedoraproject.org") - <time datetime="2013-03-04 11:41:30">Mar 1, 2013</time>

What I do normally is go to a tty, type export DISPLAY=:0; gnome-shell --replace I get a lot of weird gnome shell lockups and stuff like this around the screensaver lock dialog. And I'm still in F17.
<hr />
####
[chuck]( "chuck@chuckfrain.net") - <time datetime="2013-03-04 11:50:51">Mar 1, 2013</time>

There is a bug entered against F18 and upstream about this but I don't know what it is off hand. What I've done when I run into it is the CTRL+ALT+F2 login as previously mentioned. Find the PID of gnome-shell and 'kill -HUP PID' and it restarts fine. The root cause of my issue was using synergy and having my mouse and keyboard focus on a different screen when the screensaver kicks in. The easy solution is if you know it might kick in, leave the mouse on the main screen when you walk away. About 2 weeks ago I did a yum update on F18 and the problem went away.
<hr />
####
[surukume](http://gravatar.com/surukume "surkum@gmail.com") - <time datetime="2013-03-04 12:18:43">Mar 1, 2013</time>

CTRL+ALT+F2 login killall -HUP gnome-shell CRTL+D sometimes it works :) ,hope it gets fixed soon.
<hr />
####
[ArcFi]( "arcfi.x@gmail.com") - <time datetime="2013-03-04 12:22:25">Mar 1, 2013</time>

Alt+Ctrl+F2: pkill -3 gnome-shell Optionally: pkill gvfsd-sftp pkill gvfsd-smb
<hr />
####
[ssam]( "samtygier@yahoo.co.uk") - <time datetime="2013-03-04 12:45:23">Mar 1, 2013</time>

sudo yum install @mate-desktop
<hr />
####
[emad]( "emadalavi15@yahoo.com") - <time datetime="2013-03-04 12:47:07">Mar 1, 2013</time>

Linux desktop is dead. For your server or experiments with linux you can use XFCE or even lighter DEs.
<hr />
####
[Mike]( "spam@mindless.com") - <time datetime="2013-03-04 14:12:06">Mar 1, 2013</time>

Is an Alt-F2 + "r" strong enough to reset this? I have a lot of glitches with the audio and network applets not showing the correct status and this usually corrects things for me.
<hr />
####
[anthonyvenable110](http://anthonyvenable110.wordpress.com "anthonyvenable110@gmail.com") - <time datetime="2013-03-04 19:56:04">Mar 1, 2013</time>

Reblogged this on [anthonyvenable110](http://anthonyvenable110.wordpress.com/2013/03/04/gnome-3-why-do-you-hate-me/).
<hr />
####
[Mark]( "reiki33@yahoo.com") - <time datetime="2013-03-05 01:04:57">Mar 2, 2013</time>

Generally I like Gnome 3. For me, strangeness appears around alt-tab. With 12 to 18 windows open, alt-tab or activities to select a window starts to fragment colors, and shortly the desktop freezes. I have had similar issues on Ubuntu 12.10 with alt-tab and a triangle of a solid color from the upper left of the left monitor across to about the middle of the right monitor. The mouse will respond, but not the keyboard. Then the mouse quits responding.
<hr />
