---
title: 'Network performance'
date: Tue, 13 Sep 2016 04:01:31 +0000
draft: false
tags: [802.11n, dd-wrt, netgear, wireless]
categories: [Technology]
type: post
---

Recently I had some network issues at work with lower than normal speeds, narrowed it down to the D-Link switch. I rebooted it and things seemed to be back to normal. Then at home I was hitting some similar performance issues both wired and wireless. First thing was to verify that the wall port was giving me the correct speeds, then through the switch. Bingo, speeds were dropping. Ensured I was using Cat6 cables, found one cable that just didn't want to connect, threw it out. Then I used the [IT Crowd](https://en.wikipedia.org/wiki/The_IT_Crowd) mantra and [tried turning it off and on again](https://www.youtube.com/watch?v=p85xwZ_OLX0). Speeds were back to normal. Rebooted the downstairs switch as well, used `iperf` to measure the wired performance, **935 Mbits/sec.**```
$ iperf -p 2222 -c 172.31.6.3
------------------------------------------------------------
Client connecting to 172.31.6.3, TCP port 2222
TCP window size: 85.0 KByte (default)
------------------------------------------------------------
\[  3\] local 172.31.6.221 port 35464 connected with 172.31.6.3 port 2222
\[ ID\] Interval       Transfer     Bandwidth
\[  3\]  0.0-10.0 sec  1.09 GBytes   935 Mbits/sec
$ iperf -p 2222 -c 172.31.6.3
------------------------------------------------------------
Client connecting to 172.31.6.3, TCP port 2222
TCP window size: 85.0 KByte (default)
------------------------------------------------------------
\[  3\] local 172.31.6.221 port 35470 connected with 172.31.6.3 port 2222
\[ ID\] Interval       Transfer     Bandwidth
\[  3\]  0.0-10.0 sec  1.09 GBytes   935 Mbits/sec

```So wired performance fixed. Next up was the wireless. I was getting **8.3MBps**/**66.4 Mbps**, second run **7.0MBps**/**56Mbps**. Reading the [dd-wrt](http://www.dd-wrt.com/site/index) [docs it reads](http://www.dd-wrt.com/wiki/index.php/Netgear_WNDR3700#FAQ):

> You must use HT40 channel width & WPA2 AES when encrypting your wireless connection, otherwise the router will fallback to 802.11a/g speeds since WPA2 AES is a mandatory requirement of 802.11n specification as WPA2 AES is the only approved encryption method in the 802.11n standard.

Security was already WPA2 AES, but the Channel Width was set to the [dd-wrt](http://www.dd-wrt.com/site/index) default of Full (20MHz). I changed it to Wide HT40 (40 MHz). Rebooted the router, and gave the tests another go. First I used `dd` and `nc` then `iperf`. The `dd` reported **13.7MBps**/**109.6Mbps**.```
$ dd if=/dev/zero bs=1024K count=512 | nc -v 172.31.6.3 2222
Ncat: Version 7.12 ( https://nmap.org/ncat )
Ncat: Connected to 172.31.6.3:2222.
512+0 records in
512+0 records out
536870912 bytes (537 MB, 512 MiB) copied, 39.1152 s, 13.7 MB/s
Ncat: 536870912 bytes sent, 0 bytes received in 39.32 seconds.

````iperf` results in similar results if only slightly slower.```
$ iperf -p 2222 -c 172.31.6.3
------------------------------------------------------------
Client connecting to 172.31.6.3, TCP port 2222
TCP window size: 85.0 KByte (default)
------------------------------------------------------------
\[  3\] local 172.31.6.211 port 52358 connected with 172.31.6.3 port 2222
\[ ID\] Interval       Transfer     Bandwidth
\[  3\]  0.0-10.0 sec   110 MBytes  92.2 Mbits/sec
$ iperf -p 2222 -c 172.31.6.3
------------------------------------------------------------
Client connecting to 172.31.6.3, TCP port 2222
TCP window size: 85.0 KByte (default)
------------------------------------------------------------
\[  3\] local 172.31.6.211 port 52360 connected with 172.31.6.3 port 2222
\[ ID\] Interval       Transfer     Bandwidth
\[  3\]  0.0-10.0 sec   102 MBytes  85.0 Mbits/sec

```Two runs resulted in 92.2Mbps and 85.0Mbps. The three runs average out to **95.6Mbps** wireless. While not bad wireless performance, I was hoping to get closer to the 300Mbps product rating. **Network Hardware:**

*   Netgear WNDR3700v4 running DD-WRT v3.0-r30385 std (08/12/16)
*   [TRENDnet Gigabit switch TEG-S80DG](https://www.amazon.com/dp/B0033GFH2E/ref=pe_175190_21431760_M3T1_SC_dp_2)
*   [D-Link Gigabit switch DGS-2208](https://www.amazon.com/gp/product/B000FITKK8/ref=oh_aui_search_detailpage?ie=UTF8&psc=1)

**Computers:**

*   Lenovo T460S
*   homebuilt server, MSI 785GTM-E45 motherboard with gigabit port