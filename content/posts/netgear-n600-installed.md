---
title: 'Netgear N600 installed'
date: Sun, 29 May 2011 02:35:49 +0000
draft: false
tags: [Linux, Technology]
categories: [Linux, Technology]
type: post
---

I intended to replace our [Linksys WRT54g](http://en.wikipedia.org/wiki/Linksys_WRT54G_series) with the [Netgear N600 WNDR3700v2](http://www.netgear.com/home/products/wirelessrouters/high-performance/WNDR3700.aspx) but I didn't have the [success I wanted with dd-wrt](http://zeusville.wordpress.com/2011/05/25/netgear-n600-wndr3700v2-and-dd-wrt/) and the stock firmware doesn't offer the features like DNS, static DHCP, etc that [Tomato](http://www.polarcloud.com/tomato) and [dd-wrt](http://www.dd-wrt.com/site/index) have.

I asked myself "where do we use the wireless the most?" The answer is downstairs. I decided to host the Netgear router downstairs in the home theater cabinet. Finally I turned off the wireless on the WRT54g and keeping it as our router. Now the Mac Book Pro and the Thinkpad get **104+Mbps** vs the 5Mbps I was getting before.
---
### Comments:
#### 
[jesus m rodriguez](http://zeusville.wordpress.com "jmrodri@gmail.com") - <time datetime="2011-05-30 07:50:45">May 1, 2011</time>

Felix, no I didn't try OpenWRT. After I went back to stock firmware and decided to put the router downstairs, I didn't see the need. Maybe if I get bored again I'll give it shot.
<hr />
#### 
[Felix](http://fetzig.org "heffer@fedoraproject.org") - <time datetime="2011-05-30 05:34:34">May 1, 2011</time>

Have you tried using OpenWRT instead? For me it has great performance and one of the lead developers is a developer of ath9k, too. So it's highly optimized for these kind of devices. I use it on my D-Link DIR-825, which hardware-wise is almost the same as the WNDR3700 (I just thought the possibility of installing external antennas to the DIR-825 was more appealing :)).
<hr />
