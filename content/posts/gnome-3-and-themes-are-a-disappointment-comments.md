---
title: 'Gnome 3 and themes are a disappointment'
date: Wed, 13 Feb 2013 16:17:35 +0000
draft: false
tags: [Linux, Technology]
categories: [Linux, Technology]
type: post
---


#### 
[Andreas Nilsson](http://gravatar.com/calmcountry "andreas@andreasn.se") - <time datetime="2013-02-13 18:42:38">Feb 3, 2013</time>

Mairin, I think the crux here is that gtk2 adwaita dont have a dark variant, so someone would have to write and put that in gnome-themes-standard first.
<hr />
#### 
[Máirín Duffy](http://blog.linuxgrrl.com "duffy@fedoraproject.org") - <time datetime="2013-02-13 17:57:03">Feb 3, 2013</time>

Andreas, would it be a reasonable RFE against the tweak-tool when users select a dark theme to have it not only apply Adawaita dark to GTK3 but apply a dark theme to the equivalent / default GTK 2 theme (I'm guessing, clearlooks maybe?) I think that would have solved most of Jesus' issue, and that's the behavior I would expect from such a setting.
<hr />
#### 
[Juan Rodriguez](http://k3rnel.net "nushio@fedoraproject.org") - <time datetime="2013-02-13 12:22:45">Feb 3, 2013</time>

I'm usually not someone that would defend Gnome, but in the specific examples you mentioned, I don't think it's really Gnome's fault. Chrome uses its own whateverish Window Manager / Theme Engine, so you'd have to set up a Dark Chrome Theme. (Can't help you there, I'm a Firefox Fanboy). I'm not familiar with XChat, but is it built with gtk3? Basically, any app that doesn't use GTK3, isn't gonna go Dark. What you need in this case, is to get a matching GTK2 Dark Theme, to force Thunderbird, Firefox and the rest of the GTK2 apps to go lights out.
<hr />
#### 
[Juanjo Marin](http://gravatar.com/jjmarin96 "juanjomarin96@yahoo.es") - <time datetime="2013-02-13 13:10:46">Feb 3, 2013</time>

Which is the number of the bugzilla report about this issue ?
<hr />
#### 
[Andreas Nilsson](http://gravatar.com/calmcountry "andreas@andreasn.se") - <time datetime="2013-02-13 16:02:19">Feb 3, 2013</time>

Chrome, X-chat and Thunderbird \[1\] still uses GTK+ 2.x. The dark variant of Adwaita is only avaible for GTK3. 1. https://bugzilla.mozilla.org/show\_bug.cgi?id=627699 needs to be fixed first.
<hr />
#### 
[Andreas Nilsson](http://gravatar.com/calmcountry "andreas@andreasn.se") - <time datetime="2013-02-13 16:05:29">Feb 3, 2013</time>

If SAMBA and printing works flawlessly out of the box, but theming don't, I feel like we've got our priorities right. It used to be the other way around. ;)
<hr />
#### 
[Martin](http://mso-chronicles.blogspot.com "mso@fedoraproject.org") - <time datetime="2013-02-13 16:14:38">Feb 3, 2013</time>

Well, I'm not sure the all-dark switch is the way to go. Better go all out and find a theme that's dark from the start and has both gtk2 and gtk3 variant. (I have never been a fan of the bright/dark combination introduced in gtk3 and prefer the theme to be consistent throughout -- i.e. either all bright or all dark, having two sub-themes in one theme brings more issues than positives :-/) Then you'll probably see the correct colours everywhere (only apps with their own theme-ing will have to be changed individually).
<hr />
#### 
[liam]( "liam@fightingcrane.com") - <time datetime="2013-02-13 16:26:56">Feb 3, 2013</time>

It's unfortunate but Gnome designers don't have great "eyes". While I wouldn't say they are terrible I think they clearly have no flair. That wouldn't be much of an issue if theming were easier (and didn't break all the damn time from update to update; b/c of that we lost half-left \[http://half-left.deviantart.com/journal/GTK3-Themes-307026665\], one of the more talented themers for gnome, who certainly has shown a better sense of design than anything the gnome designers have given us), or the default theme were "nicer" but neither of those is the case. I really wish the folks at gnome would focus more on stability between major releases. As others have said, the model they should look towards is gstreamer.
<hr />
#### 
[Kevin Kofler](http://www.tigen.org/kevin.kofler/ "kevin.kofler@chello.at") - <time datetime="2013-02-17 06:32:02">Feb 0, 2013</time>

You don't even need a different theme for GTK+ 2, just a different color scheme! The "use dark theme" option should enforce a dark color scheme across all apps through whatever mechanism (XSettings, gtkrc etc.) that works.
<hr />
#### 
[anthonyvenable110](http://anthonyvenable110.wordpress.com "anthonyvenable110@gmail.com") - <time datetime="2013-02-13 20:35:56">Feb 3, 2013</time>

Reblogged this on [anthonyvenable110](http://anthonyvenable110.wordpress.com/2013/02/13/1994/).
<hr />
#### 
[test 123]( "test123@gmail.com") - <time datetime="2013-02-13 22:15:46">Feb 3, 2013</time>

I think Gnom3 is quite possibly the best piece of software ever written.
<hr />
#### 
[jdanielcampos](http://jdanielcampos.wordpress.com "camposjorge@outlook.com") - <time datetime="2013-02-14 00:46:36">Feb 4, 2013</time>

I think you could tweak the theme a bit, can't you? I mean there's always downloading the human theme from synaptic package manager, and changing the colors of it to black. But I haven't tried GNOME 3 for the fact that I never felt I needed to upgrade to it... I've stayed with GNOME 2.28 since Ubuntu 10.04 LTS was available and never have had any problems other than my gpu not being supported and having to manually configure the xorg.conf file to enable wobbly windows and etc.
<hr />
#### 
[nicubunu](http://nicubunu.blogspot.com/ "nicubunu@gmail.com") - <time datetime="2013-02-14 06:42:26">Feb 4, 2013</time>

@Andreas, actually the people working on SAMBA, printing, kernel are totally different from those making themes :) But you know that.... anyway, you raised my ball: if the Anaconda is broken and can't install the damn thing, themes, printing, whatever, all is useless
<hr />
#### 
[Andrew Clunis](http://www.orospakr.ca/ "andrew@orospakr.ca") - <time datetime="2013-02-14 13:37:28">Feb 4, 2013</time>

This is how I deal with the GTK2 apps: ln -s /usr/share/themes/Darklooks/gtk-2.0/gtkrc ~/.gtkrc-2.0
<hr />
#### 
[Claus Jordan]( "amazoniac@leftbehind.com") - <time datetime="2013-02-14 15:15:01">Feb 4, 2013</time>

I stopped using Gnome long time ago. I thing they never improve the look and feel of the desktop as KDE do.
<hr />
