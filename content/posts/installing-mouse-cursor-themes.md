---
title: 'Installing mouse cursor themes'
date: Tue, 30 Aug 2005 20:40:17 +0000
draft: false
tags: [Linux]
categories: [Linux]
type: post
---

The following was posted by jodrell@spod.uk.net on 2003-09-19 09:36:52 +(-23)-

If your system uses XFree86 4.3.0 or higher and you want to use a snazzy alpha-channeled mouse cursor theme, here's how you do it:

1\. Create a directory in your home called .icons. This is the directory defined by the Freedesktop.org standards as the place for user-defined icon themes.

2\. Place the cursor theme directory into ~/.icons. The directory should have the form ~/.icons/THEME\_NAME/cursors.

3\. With either gconftool or gconf-editor, set the value of /desktop/gnome/peripherals/mouse/cursor\_theme to the name of the new theme.

4\. If you use another window manager or desktop environment, you can also place a line like this in ~/.Xdefaults:

```
    Xcursor.theme:THEME\_NAME

```or you can set the XCURSOR\_THEME environment variable in your startup scripts.

You can find cursor themes at the following addresses:

*   [http://kde-look.org/?xcontentmode=mouse](http://kde-look.org/?xcontentmode=mouse)
*   [http://themedepot.org/showarea.php4?area=19](http://themedepot.org/showarea.php4?area=19)
*   [http://themes.freshmeat.net/browse/982/?topic\_id=982](http://themes.freshmeat.net/browse/982/?topic_id=982)
*   [http://www.gnome-look.org/index.php?xcontentmode=36&PHPSESSID=29781ed96d065b2ae16800b8682d82d6](http://www.gnome-look.org/index.php?xcontentmode=36&PHPSESSID=29781ed96d065b2ae16800b8682d82d6)

...  
Read [more](http://gnome-hacks.jodrell.net/hacks.html?id=30).