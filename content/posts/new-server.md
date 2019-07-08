---
title: 'new server'
date: Thu, 03 Jun 2010 13:50:44 +0000
draft: false
tags: [Linux, Technology]
type: post
---

I have a file server at home with two 250GB hard drives running in RAID1. It is meant for storing my backups and acts as a [DLNA](http://www.dlna.org/home) server for my [PlayStation 3](http://us.playstation.com/ps3/index.htm). Unfortunately, I fell into the same trap as most folks thought [Bill Gates](http://en.wikiquote.org/wiki/Bill_Gates#Misattributed) did, when I told myself that 250GB should be enough data for anyone. Apparently backup data, music and pictures take up a lot of room as you can see from my /vol partition.```
$ df -h
Filesystem    Type    Size  Used Avail Use% Mounted on
/dev/mapper/vol1-lvvol
              ext3    226G  214G  641M 100% /vol

```I figured it was time for an upgrade. I replaced motherboard, cpu, memory, and of course the drives. The old machine specs are as follows:

*   Pentium III 933MHz
*   1 GB memory
*   two 40GB IDE hard drives RAID1 hosting /
*   two 250GB Seagate 7200.10 SATA drives RAID1 hosting /vol
*   [megabit](http://en.wikipedia.org/wiki/Megabit) NIC

The new machine has [TERABYTE](http://en.wikipedia.org/wiki/Terabyte) drives :)

*   [AMD Sempron 140 2.7GHz](http://www.newegg.com/Product/Product.aspx?Item=N82E16819103698)
*   2GB memory
*   one 80GB Western Digital SATA drive hosting /
*   three [1TB](http://www.newegg.com/Product/Product.aspx?Item=N82E16822152185) Samsung Spinpoint SATA drives RAID5 hosting /vol
*   [gigabit](http://en.wikipedia.org/wiki/Gigabit) NIC
It was fun to see T after the number for the /vol partition.```
\# df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/mapper/vg1-lvroot
                       70G  2.8G   64G   5% /
tmpfs                 878M  128K  878M   1% /dev/shm
/dev/sda1             485M   28M  432M   7% /boot
/dev/mapper/vg2-lvvol
                      1.8T  196M  1.7T   1% /vol

```Finally, the OS install experience. I wanted to use [CentOS](http://centos.org/) 5.5 for my new server. I start with the CD netinstall disk of CentOS, got to the point of writing to the partitions and the installer just died. I then went with the CentOS LiveCD and that didn't even boot for me. Stumped, and not wanting to wait for CentOS to download stage2.img again (took 15 minutes), I decided to try the Fedora 13 netinstall CD. WIN! The Fedora 13 installation went flawlessly and extremely quick boot, and a very nice experience. Kudos to the Fedora team for an excellent installation experience. ![new server](http://farm2.static.flickr.com/1269/4662655035_8d3f990186.jpg) ![drive cage](http://farm5.static.flickr.com/4050/4662654503_7ab23c6b0e.jpg)