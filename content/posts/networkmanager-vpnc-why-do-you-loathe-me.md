---
title: 'NetworkManager VPNC why do you loathe me?'
date: Tue, 27 Mar 2012 13:19:55 +0000
draft: false
tags: [Linux]
categories: [Linux]
type: post
---

For some reason on Fedora 16, NetworkManager VPNC dialog won't appear as expected. When I click the VPN Connection from the menu, nothing appears. I have to kill the `/usr/libexec/nm-vpnc-auth-dialog` process twice before it actually displays the prompt. This happens every time I want to use vpnc from the NetworkManager drop-down. I'll be experimenting to see if this occurs after reboot or just from suspend.