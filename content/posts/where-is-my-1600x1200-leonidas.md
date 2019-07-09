---
title: 'Where is my 1600x1200 Leonidas?'
date: Sun, 26 Jul 2009 16:13:55 +0000
draft: false
tags: [Linux]
categories: [Linux]
type: post
---

After upgrading both my Thinkpad T43 laptop and Dell workstation to Fedora 11, I decided to upgrade my home machine from Fedora 9 to 11. Actually it wasn't a traditional upgrade, it was a reinstall. The hardest part about the installation has been trying to figure out all of the things I needed to backup.

I rsync'd /etc/, $HOME, and some scripts I had in /opt over to my server and proceeded to wipe the box clean. This time I chose to partition the drive so that /home is in a separate partition, hopefully this will make it easier to upgrade/install in the future.  The installer seemed more streamlined than previous versions, less questions, either that or I'm just used to clicking through it without paying much attention :) Once I selected the packages to install I left it copying data overnight.

The following morning I rebooted and logged in via the command line to start the rsync of my data back to the machine. After several hours of data copying, and package installation I was up and running. All is well except for my screen resolution, the new 'enhancements' won't detect that my monitor can do 1600x1200, so it limits me to a paltry 1280x1024. Using xrandr I was able to add a new modeline, then changed the resolution to 1600x1200.

`$ gtf 1600 1200 70`

`# 1600x1200 @ 70.00 Hz (GTF) hsync: 87.43 kHz; pclk: 190.25 MHz`

`Modeline "1600x1200_70.00" 190.25 1600 1712 1888 2176 1200 1201 1204 1249 -HSync +Vsync`

`xrandr --newmode "1600x1200_70.00" 190.25 1600 1712 1888 2176 1200 1201 1204 1249 -HSync +Vsync`

`xrandr --addmode VGA-0 "1600x1200_70.00"`

This is great except I have to do this every time I login. Before I figured out xrandr, I tried using system-config-display which created an xorg.conf (which in Fedora 11 is gone now).  After rebooting with the 'generated' config, the machine was stuck showing me a blue screen with the fedora logo in it. I had to boot up in rescue mode to be able to see what was going on. Xorg.0.log showed the following:

`(WW) xf86CloseConsole: KDSETMODE failed: Bad file descriptor`

`(WW) xf86CloseConsole: VT_GETMODE failed: Bad file descriptor`

Hrm something is wrong with my 'generated' xorg.conf, maybe that's the reason system-config-display isn't installed by default :)

```
\# Xorg configuration created by system-config-display

Section "ServerLayout"

    Identifier     "single head configuration"

    Screen      0  "Screen0" 0 0

    InputDevice    "Keyboard0" "CoreKeyboard"

EndSection

Section "InputDevice"

# keyboard added by rhpxl

    Identifier  "Keyboard0"

    Driver      "kbd"

    Option      "XkbModel" "pc105+inet"

    Option      "XkbLayout" "us"

EndSection

Section "Monitor"

    Identifier   "Monitor0"

    ModelName    "NEC MultiSync E900+"

    HorizSync    31.0 - 96.0

    VertRefresh  55.0 - 160.0

    Option      "dpms"

EndSection

Section "Device"

    Identifier  "Videocard0"

    Driver      "radeon"

EndSection

Section "Screen"

    Identifier "Screen0"

    Device     "Videocard0"

    Monitor    "Monitor0"

    DefaultDepth     24

    Modeline "1600x1200"  190.50  1600 1720 1888 2176  1200 1203 1207 1252 -hsync +vsync

    Option "PreferredMode" "1600x1200"

    SubSection "Display"

        Viewport   0 0

        Depth     24

    EndSubSection

EndSection

I wasn't in the mood to figure out the problem right then, so I did the obvious: mv xorg.conf dontusethisxorg\_conf and rebooted. This time it booted up to the gdm login screen, sadly at the crappy 1152x768 resolution. Right now I'm just staying logged in :) until I can figure out what the heck is wrong and how to specify the information properly in xorg.conf.

**Hardware**

*   ATI Technologies Inc RV370 5B60 \[Radeon X300 (PCIE)\]

*   NEC Multisync E900+ 19" CRT (yes it's still a CRT, I really want a **[Dell Ultrasharp 2408WFP LCD](http://accessories.us.dell.com/sna/products/Monitors/productdetail.aspx?c=us&l=en&s=dhs&cs=19&sku=320-6272)!**)

*   monitor is connected to the ATI via VGA connection

I'll keep digging to see how to get this working after reboots, if anyone has any suggestions feel free to leave me a comment.


```
---
### Comments:
#### [mpdehaan](http://michaeldehaan.net "michael.dehaan@gmail.com") - <time datetime="2009-07-26 14:19:39">Jul 0, 2009</time>

I think on one of my systems (forget which, I think the "home" development setup but might have been the work one -- I think that monitor had a weirder aspect ratio), I ended up setting up xrandr to run on GNOME startup as an custom trigger/script, for similar reasons. Can't remember if I got it fixed correctly or not :)
<hr />
#### [ank]( "ank@ya.ru") - <time datetime="2009-07-26 18:45:34">Jul 0, 2009</time>

I have similar config except this line: Modes "1600x1200" inside Subsection "Display" After reboot system-config-display picks up new resolution.
<hr />
#### [Adam Williamson](http://www.happyassassin.net "adamwill@shaw.ca") - <time datetime="2009-07-27 19:43:26">Jul 1, 2009</time>

The modeline and preferredmode lines are supposed to go in the Monitor section, not the Screen section. http://wiki.debian.org/XStrikeForce/HowToRandR12 is pretty much the bible for all things RandR 1.2 :)
<hr />
