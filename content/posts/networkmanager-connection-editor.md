---
title: 'NetworkManager connection editor'
date: Sun, 28 Aug 2011 13:49:42 +0000
draft: false
tags: [Linux, Technology]
categories: [Linux, Technology]
type: post
---

I had two problems with my network connections in NetworkManager. The first was at work it would

auto-connect to the guest network which I unintentionally tried ONCE. That's all it took to become

annoying. The second problem was at home, I switched my network from WEP to WPA2 and couldn't

get find a way to change it to use WPA2 so I could enter the password.

In the past, I could access the NetworkManager connection editor from the nm-applet, but in

Fedora 15 I couldn't figure it out. I tried using the 'Network Settings' from the menu.

[![](/img/2011/08/menu.png "menu")](/img/2011/08/menu.png)

But that would bring up the pretty useless network settings screen.

[![](/img/2011/08/network-settings.png "network-settings")](/img/2011/08/network-settings.png)

There's no way to edit the connection information there. I wanted to remove some of the networks NetworkManager remembered. Thanks to Google, I was able to find a [post that mentioned to use](http://mail.gnome.org/archives/networkmanager-list/2009-January/msg00265.html) `nm-connection-editor`.

If you need or want to edit your network connections in NetworkManager, you will need to

run `nm-connection-editor`. You'll have to run it from the terminal since there's

no way to get at it from the GUI, not even from the Applications menu.

[![](/img/2011/08/nm-connection-editor.png "nm-connection-editor")](/img/2011/08/nm-connection-editor.png)

Once there I was able to go to the Wireless tab, remove the stupid networks. Change the

guest network at work to not auto connect, and change the security type from my home network.
---
### Comments:
#### [lzap](http://gravatar.com/lzap "lzap@seznam.cz") - <time datetime="2011-08-28 13:31:39">Aug 0, 2011</time>

I wonder if this ever hits version 1.0...
<hr />
#### [robinnorwood](http://gravatar.com/robinnorwood "robin.norwood@gmail.com") - <time datetime="2011-08-28 16:27:26">Aug 0, 2011</time>

Yeah, ran into the same issue. Usability #fail!
<hr />
#### [Juan Rodriguez](http://k3rnel.net "nushio@fedoraproject.org") - <time datetime="2011-08-28 17:38:24">Aug 0, 2011</time>

Typical Gnome for ya. I switched to KDE because of the Shell Fiasco and do have easy access to the same dialog (but built in QT instead of GTK). Btw, there is a way to access that, IIRC. I remember using Gnome 3 for a few weeks and accidentally discovered how. Click on Network Settings, Then on Wireless, then when you select Networks, IIRC, there was an option called "Other" or something like that, that would open the dialog. I might be mistaken and my memory is playing tricks on me. I mostly remember blind rage during my Gnome 3 usage period.
<hr />
#### [liam]( "liam@fightingcrane.com") - <time datetime="2011-08-29 01:07:10">Aug 1, 2011</time>

That only works if you are ALREADY connected. Yeah, not great.
<hr />
#### [Diego]( "diegob08@yahoo.com.ar") - <time datetime="2011-08-28 22:57:27">Aug 0, 2011</time>

I had a similar problem and to edit the connections just as you do without using the terminal, I opened the Activities menu and typed "red" (network in Spanish) and it gave me 2 options. RED and CONEXIONES DE RED, Network and Network Connections. The second is the one that you needed.
<hr />
#### [Adam Williamson](http://www.happyassassin.net "awilliam@redhat.com") - <time datetime="2011-08-29 17:35:43">Aug 1, 2011</time>

"Thanks to Google, I was able to find a post that mentioned to use nm-connection-editor." Always read the errata! https://fedoraproject.org/wiki/Common\_F15\_bugs#networkmanager\_shell
<hr />
