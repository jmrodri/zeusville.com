---
title: 'NetworkManager connection editor'
date: Sun, 28 Aug 2011 13:49:42 +0000
draft: false
tags: [Linux, Technology]
type: post
---

I had two problems with my network connections in NetworkManager. The first was at work it would auto-connect to the guest network which I unintentionally tried ONCE. That's all it took to become annoying. The second problem was at home, I switched my network from WEP to WPA2 and couldn't get find a way to change it to use WPA2 so I could enter the password. In the past, I could access the NetworkManager connection editor from the nm-applet, but in Fedora 15 I couldn't figure it out. I tried using the 'Network Settings' from the menu. [![](http://zeusville.files.wordpress.com/2011/08/menu.png "menu")](http://zeusville.files.wordpress.com/2011/08/menu.png) But that would bring up the pretty useless network settings screen. [![](http://zeusville.files.wordpress.com/2011/08/network-settings.png "network-settings")](http://zeusville.files.wordpress.com/2011/08/network-settings.png) There's no way to edit the connection information there. I wanted to remove some of the networks NetworkManager remembered. Thanks to Google, I was able to find a [post that mentioned to use](http://mail.gnome.org/archives/networkmanager-list/2009-January/msg00265.html) `nm-connection-editor`. If you need or want to edit your network connections in NetworkManager, you will need to run `nm-connection-editor`. You'll have to run it from the terminal since there's no way to get at it from the GUI, not even from the Applications menu. [![](http://zeusville.files.wordpress.com/2011/08/nm-connection-editor.png "nm-connection-editor")](http://zeusville.files.wordpress.com/2011/08/nm-connection-editor.png) Once there I was able to go to the Wireless tab, remove the stupid networks. Change the guest network at work to not auto connect, and change the security type from my home network.