---
title: 'networking saga (parte dos)'
date: Wed, 15 Nov 2006 04:26:00 +0000
draft: false
tags: [Linux]
categories: [Linux]
type: post
---

I spent 2 hours and 15 minutes on the phone with my father-in-law helping him get the [Linksys WAP54G](http://www.linksys.com/servlet/Satellite?c=L_Product_C2&childpagename=US%2FLayout&cid=1126536803676&pagename=Linksys%2FCommon%2FVisitorWrapper) connected to his [Linksys WRT54G](http://www.linksys.com/servlet/Satellite?c=L_Product_C2&childpagename=US%2FLayout&cid=1149562300349&pagename=Linksys%2FCommon%2FVisitorWrapper) router. I set it up at my house first so I got get the steps down, and since it was configured for DHCP, I assumed it would get an address once he got it home.  WRONG!

After several resets, both 30 and 60 seconds, I gave up and contacted technical support.  So here I am doing a live chat with Linksys technical support while on the phone with my father-in-law passing him the commands to run.  I had a PC connected to the router, and the access point connected to the router.  Turns out you can connect the PC directly to the access point and configure it at the base ip address of 192.168.1.245 (after a 30 second reset with the power on of  course).

Once we got the access point configured as a wireless repeater, we unplugged it, and moved it downstairs to the basement.  Plugged it into the wall for power, and all lights indicated a go.  We logged on to the machine downstairs (about 10 feet from the access point), and saw the wireless connection utility say "Very Low 11Mbps".  I was about to flip my lid as we were at the 2 hour mark already. I had him disconnect from his network, and refresh the list of available networks. We then saw 4 out of 5 bars.  I was getting happier but didn't want to get my hopes up yet.  I asked him to connect to that one.  BINGO!  Connection utility reported "Excellent 54Mbps". ROCK ON!

Somedays I hate being a computer geek in a family of non-geeks.  Ah, who am I kidding, I love this stuff.