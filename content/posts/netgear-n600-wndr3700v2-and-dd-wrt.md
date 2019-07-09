---
title: 'Netgear N600 WNDR3700v2 and dd-wrt'
date: Thu, 26 May 2011 02:25:28 +0000
draft: false
tags: [Linux, Technology]
categories: [Linux, Technology]
type: post
---

Since the default Netgear firmware doesn't have DNS built in, I flashed the [WNDR3700](http://www.dd-wrt.com/wiki/index.php/Netgear_WNDR3700)

with dd-wrt. But I was thoroughly disappointed with the performance even after following the settings from the wiki for the [Atheros](http://www.dd-wrt.com/wiki/index.php/Atheros/ath_wireless_settings) wireless settings.

**netgear wireless n (5Ghz) 2ft ddwrt**

78.2539s

6.9 MB/s

55.2Mbps

**netgear wireless n (2.4Ghz) 2ft ddwrt**

61.0922s

8.8 MB/s

70.4Mbps

**netgear wireless n (5Ghz) 2ft ddwrt turbo mode**

51.4871s

10.4MB/s

**83.2Mbps**

**netgear wireless n (5Ghz) 2ft ddwrt turbo mode + tuning**

52.51s

10.2MB/s

81.6Mbps

**netgear wireless n (5Ghz) downstairs ddwrt turbo mode + tuning**

272.237s

2.0MB/s

16.0Mbps

**netgear wireless n (2.4Ghz) downstairs ddwrt turbo mode + tuning**

226.537s

2.4MB/s

**19.2Mbps**

Clearly the **tuning** didn't actually help, and the fastest I could get was 83.2Mbps but I got 123.2Mbps with the stock firmware. I reset the router back to factory defaults and was able to get 104.8Mbps which is still slower than it was before but it's way better than dd-wrt.

This is definitely disappointing since I had such great success with [Tomato](http://www.polarcloud.com/tomato) firmware on my WRT54G.
---
### Comments:
####
[Netgear N600 installed &laquo; zeusville](http://zeusville.wordpress.com/2011/05/28/netgear-n600-installed/ "") - <time datetime="2011-05-28 22:36:10">May 6, 2011</time>

\[...\] intended to replace our Linksys WRT54g with the Netgear N600 WNDR3700v2 but I didn’t have the success I wanted with dd-wrt and the stock firmware doesn’t offer the features like DNS, static DHCP, etc that Tomato and \[...\]
<hr />
####
[hbt]( "horrex@gmail.com") - <time datetime="2011-05-26 02:39:32">May 4, 2011</time>

you might wanna check openwrt. the guy hacking for atheros/qualcomm on ath9k is maintaining lots of stuff there.
<hr />
####
[Stephen Smoogen]( "smooge@gmail.com") - <time datetime="2011-05-26 12:22:53">May 4, 2011</time>

Wireless being a 'switchless' technology is going to see inconsistent speed issues depending on multiple factors: 1) Slowest system on network can affect speed for all other systems 2) Conflicting frequencies can affect speed due to retransmits 3) Various buffer-bloat items so that certain traffic gets high throughput for a short while but much slower throughput long ter,
<hr />
####
[bretm](http://bretm.wordpress.com/ "bret.mcmillan@gmail.com") - <time datetime="2012-01-28 19:10:26">Jan 6, 2012</time>

It looks like your testing of dd-wrt was only ever w/ 40mhz (turbo)... how was the stock firmware configured? Did it use 20/40, 20, or 40mhz? That can really make a difference depending upon how much interference you're getting...
<hr />
