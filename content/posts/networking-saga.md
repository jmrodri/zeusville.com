---
title: 'networking saga'
date: Mon, 13 Nov 2006 00:53:45 +0000
draft: false
tags: [Personal]
type: post
---

After [spending Sunday afternoon setting up a wireless access point](http://zeusville.wordpress.com/2006/11/12/family-computer-specialist/) I decided to resurrect my wired router ([Linksys BEFSR41](http://www.linksys.com/servlet/Satellite?c=L_Product_C2&childpagename=US%2FLayout&cid=1122062340941&pagename=Linksys%2FCommon%2FVisitorWrapper)) and connect it to my wireless router ([Linksys WRT54G](http://www.linksys.com/servlet/Satellite?c=L_Product_C2&childpagename=US%2FLayout&cid=1149562300349&pagename=Linksys%2FCommon%2FVisitorWrapper)). I used up all my ports on the wireless router and didn't want to buy a hub. I tried a few months ago to get the wired router to work but to no avail. Turns out I was plugging the WAN port from the wired router to a numbered port on the wireless router. This works but creates two different networks. I wanted a single network.

The solution was to connect a numbered port from the wired router to a numbered port on the wireless router. You also need to disable DHCP on the wired router. That's it. It works great, I now have 3 free ports.