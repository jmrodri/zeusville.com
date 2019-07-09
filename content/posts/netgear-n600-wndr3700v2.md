---
title: 'Netgear N600 WNDR3700v2'
date: Wed, 25 May 2011 01:57:34 +0000
draft: false
tags: [Linux, Technology]
categories: [Linux, Technology]
type: post
---

I bought the [Netgear N600 WNDR3700](http://www.netgear.com/home/products/wirelessrouters/high-performance/WNDR3700.aspx) router to replace my aging Linksys WRT54g.

I used jbowes [method of performance](http://jbowes.wordpress.com/2010/10/13/measuring-network-speeds-with-netcat-and-dd/) testing. I ran nc on the server:

```
nc -v -l 2222 > /dev/null
```.

Then on the laptop I connected to the server via Netgear 2.4GHz, 5GHz, Linksys G, and wired running

```
dd if=/dev/zero bs=1024K count=512 | nc -v $SERVER\_IP 2222
```. For a baseline here is the gigabit wired connection.

**wired via gigabit**

4.62219 s

116 MB/s

928Mbps

Here are the preliminary wireless results with no tuning.

**Netgear N600 2ft 5GHz**

34.9444 s

15.4 MB/s

**123.2Mbps**

**Netgear N600 2ft 2.4GHz**

49.4792 s

10.9 MB/s

87.2Mbps

**Linksys WRT54g 2ft**

206.399 s

2.6 MB/s

20.8Mbps

Now I go downstairs to test again, noticeable difference:

**Netgear N600 downstairs 5GHz**

129.832 s

4.1 MB/s

32.8Mbps

**Netgear N600 downstairs 2.4GHz**

103.783 s

5.2 MB/s

**41.6Mbps**

**Linksys WRT54g downstairs**

308.374 s

1.7 MB/s

13.6Mbps

Now I'll play around with some settings to see if it makes any difference.
---
### Comments:
#### 
[Mike McCune](http://suds.org "mmccune@gmail.com") - <time datetime="2011-12-11 14:35:06">Dec 0, 2011</time>

found it handy to run it in an endless loop so you can repeat tests and not have to muck with the server: #!/bin/bash while : do nc -v -l 2222 > /dev/null done
<hr />
