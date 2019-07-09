---
title: 'Resolution problem solved'
date: Mon, 27 Jul 2009 01:23:25 +0000
draft: false
tags: [Linux]
categories: [Linux]
type: post
---

[Yesterday](http://zeusville.wordpress.com/2009/07/26/where-is-my-1600x1200-leonidas/) I posted about trying to get my old CRT to do 1600x1200 again using Fedora 11. Yesterday I had an incorrect xorg.conf, here's the correct one that is working for me. The key to my problem was adding the Modeline to the Monitor section **NOT** to the Display section. After putting this xorg.conf into action I got 1600x1200 from the gdm login screen onwards. I don't think there is any hope for the bootup screens they still show up with some awful resolution.```
\# Xorg configuration created by system-config-display

Section "ServerLayout"
	Identifier     "single head configuration"
	Screen      0  "Screen0" 0 0
	InputDevice    "Keyboard0" "CoreKeyboard"
EndSection

Section "InputDevice"
	Identifier  "Keyboard0"
	Driver      "kbd"
	Option	    "XkbModel" "pc105"
	Option	    "XkbLayout" "us+inet"
EndSection

Section "Monitor"
	Identifier   "Monitor0"
	ModelName    "NEC MultiSync E900+"
	HorizSync    31.0 - 96.0
	VertRefresh  55.0 - 160.0
	Option	    "dpms"
	Modeline "1600x1200"  190.50  1600 1720 1888 2176  1200 1203 1207 1252 -hsync +vsync
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
    
	SubSection "Display"
		Viewport   0 0
		Depth     24
		Modes    "1600x1200"
        #"1600x1024" "1440x900" "1400x1050" "1360x768" "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480" "640x400" "640x350"
	EndSubSection
EndSection

```