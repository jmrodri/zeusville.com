---
title: 'Fedora 13 install a no go'
date: Tue, 28 Sep 2010 00:45:14 +0000
draft: false
tags: [Linux, Technology]
categories: [Linux, Technology]
type: post
---


#### 
[Bucky]( "bucky@mightytikigod.com") - <time datetime="2010-09-27 21:46:06">Sep 1, 2010</time>

I haven't had this problem in Fedora (I haven't created software RAID partitions with Fedora), but the Anaconda in CentOS (in my experience) has problems mounting previously-created software RAID volumes. Verify that you can boot into Rescue mode of the Fedora 13 installer and use the mdadm command to assemble your RAID (if it's like CentOS, it will fail to do it automatically, but succeed if you generate an /etc/mdadm.conf file and run the commands yourself). If this works, then just do a regular install and carefully avoid touching the partitions which constitute your /home RAID. When you reboot into Fedora 13, reassemble your RAID with mdadm, regenerate /etc/mdadm.conf and edit /etc/fstab by hand.
<hr />
#### 
[amachina]( "amachina@cavtel.net") - <time datetime="2011-03-15 21:31:07">Mar 2, 2011</time>

I experienced the same problem. What finally worked for me is: 1) boot into rescue mode 2) execute dd if=/dev/zero of=/dev/sda
<hr />
