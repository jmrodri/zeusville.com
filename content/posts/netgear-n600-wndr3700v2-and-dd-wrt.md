---
title: 'Netgear N600 WNDR3700v2 and dd-wrt'
date: Thu, 26 May 2011 02:25:28 +0000
draft: false
tags: [Linux, Technology]
categories: [Linux, Technology]
type: post
---

Since the default Netgear firmware doesn't have DNS built in, I flashed the [WNDR3700](http://www.dd-wrt.com/wiki/index.php/Netgear_WNDR3700) with dd-wrt. But I was thoroughly disappointed with the performance even after following the settings from the wiki for the [Atheros](http://www.dd-wrt.com/wiki/index.php/Atheros/ath_wireless_settings) wireless settings.

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

Clearly the **tuning** didn't actually help, and the fastest I could get was 83.2Mbps but I got 123.2Mbps with the stock firmware. I reset the router back to factory defaults and was able to get 104.8Mbps which is still slower than it was before but it's way better than dd-wrt. This is definitely disappointing since I had such great success with [Tomato](http://www.polarcloud.com/tomato) firmware on my WRT54G.