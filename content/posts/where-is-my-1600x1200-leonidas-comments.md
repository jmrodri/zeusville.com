---
title: 'Where is my 1600x1200 Leonidas?'
date: Sun, 26 Jul 2009 16:13:55 +0000
draft: false
tags: [Linux]
---


#### 
[mpdehaan](http://michaeldehaan.net "michael.dehaan@gmail.com") - <time datetime="2009-07-26 14:19:39">Jul 0, 2009</time>

I think on one of my systems (forget which, I think the "home" development setup but might have been the work one -- I think that monitor had a weirder aspect ratio), I ended up setting up xrandr to run on GNOME startup as an custom trigger/script, for similar reasons. Can't remember if I got it fixed correctly or not :)
<hr />
#### 
[ank]( "ank@ya.ru") - <time datetime="2009-07-26 18:45:34">Jul 0, 2009</time>

I have similar config except this line: Modes "1600x1200" inside Subsection "Display" After reboot system-config-display picks up new resolution.
<hr />
#### 
[Adam Williamson](http://www.happyassassin.net "adamwill@shaw.ca") - <time datetime="2009-07-27 19:43:26">Jul 1, 2009</time>

The modeline and preferredmode lines are supposed to go in the Monitor section, not the Screen section. http://wiki.debian.org/XStrikeForce/HowToRandR12 is pretty much the bible for all things RandR 1.2 :)
<hr />
