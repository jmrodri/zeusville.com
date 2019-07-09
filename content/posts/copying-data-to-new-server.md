---
title: 'copying data to new server'
date: Fri, 04 Jun 2010 18:23:10 +0000
draft: false
tags: [Linux, Technology]
categories: [Linux, Technology]
type: post
---

As you may know I built a [new file server](http://zeusville.wordpress.com/2010/06/03/new-server/), so the logical next step is to copy over the data from the old server. I did a simple rsync but soon realized that copying 214GB over the old server's meager 100Mbps NIC was going to be painful. Not sure why but it was going very slow. Started the copy around lunch and by 5pm it had only done 30GB.

What can I do? Oh I can take out one of the drives from the old server and put it into the new one. Wait it's a RAID drive. hrm. But it's a RAID1 so I can use just one of the drives as a RAID device in degraded mode. This will surely work.

So I put the drive in the new machine. Next problem was how do I get the RAID drive as a new /dev/md2 device so I can mount the LVM partition from it to do the copy. **WORDS OF CAUTION**: if you do not know how to use _mdadm_ read up on it BEFORE you attempt to mess around with it :)

I proceeded to try out mdadm --create /dev/md2 --raid-devices=1 /dev/sde1 --force. This is **NOT** what you want to do if you want to keep the data on that drive :( No amount of lvm commands would help, which is obvious since I wiped it out. Ok now what?

I put the drive back into the old server, and since it was a RAID1, I can rebuild it. I first add the drive back to the RAID array:

```
\# mdadm --manage /dev/md1 --add /dev/sdb1

# cat /proc/mdstat

md1 : active raid1 sda1\[0\] sdb1\[1\]

      24418688 blocks \[2/1\] \[U\_\]

      \[=>...................\]  recovery =  6.4% 

I let that rebuild overnight. The next morning I move the drive back to the new server for yet another attempt at copying over the data. This time I am armed with [more information](http://www.linuxjournal.com/article/8874?page=0,1).

First let's see which drive it is:

```
\# fdisk -l

...

Disk /dev/sde: 250.1 GB, 250059350016 bytes

255 heads, 63 sectors/track, 30401 cylinders

Units = cylinders of 16065 \* 512 = 8225280 bytes

Sector size (logical/physical): 512 bytes / 512 bytes

I/O size (minimum/optimal): 512 bytes / 512 bytes

Disk identifier: 0x00075dc6

   Device Boot      Start         End      Blocks   Id  System

/dev/sde1   \*           1       30401   244196001   fd  Linux raid autodetect

...

Let's scan the drive:

```
\# mdadm --examine --scan /dev/sde1

ARRAY /dev/md2 UUID=061bae16:75f0a757:29aadef0:45edc6c0

I added the above to the bottom of /etc/mdadm.conf.

```
ARRAY /dev/md2 UUID=061bae16:75f0a757:29aadef0:45edc6c0 devices=/dev/sde1,missing
```

Then I restarted the array: 

```
\# mdadm -A -s

# cat /proc/mdstat 

Personalities : \[raid6\] \[raid5\] \[raid4\] \[raid1\] 

md2 : active raid1 sde1\[1\]

      244195904 blocks \[2/1\] \[\_U\]

md0 : active raid5 sdd1\[3\] sdb1\[0\] sdc1\[1\]

      1953518592 blocks super 1.1 level 5, 512k chunk, algorithm 2 \[3/3\] \[UUU\]

      bitmap: 2/8 pages \[8KB\], 65536KB chunk

unused devices: 

Whew done. Wait no I'm not. I still need to mount the LVM volumes. Thankfully I didn't

use the default of VolGroup00 (the default is now vg-machinename) on either of my machines. I used vol1 on the old machine and vg(0,1) on the new one. No conflicts to deal with. A quick

```
\# vgchange -a y

# mkdir /mnt/oldvol

# mount /dev/vol1/lvvol /mnt/oldvol

Let's check it:

```
\# ls /mnt/oldvol/

backups  lost+found  music

```
\# df -h

Filesystem            Size  Used Avail Use% Mounted on

/dev/mapper/vg1-lvroot

                       70G  2.9G   64G   5% /

tmpfs                 877M     0  877M   0% /dev/shm

/dev/sda1             485M   28M  432M   7% /boot

/dev/mapper/vg2-lvvol

                      1.8T   48G  1.7T   3% /vol

/dev/mapper/vol1-lvvol

                      226G  214G  641M 100% /mnt/oldvol

YAY! Now we can start copying data over the SATA bus which is rated at 3Gbps vs the NIC at 100Mbps.

Remember kids, if you don't know how to use mdadm **TREAD CAREFULLY!**


```
```
```
```
```
```
```
---
### Comments:
#### 
[Gigi]( "sgireeshmail@gmail.com") - <time datetime="2010-06-09 22:10:40">Jun 3, 2010</time>

Even if you had used the default VolGroup00, atleast on the latest fedora, vgdisplay will throw an error that "multiple vgs have the same name, so varying the one the one that was created on this machine". As long as the VGids are different, you can rename the one on the moved disk and import it. After my old laptop borked, I did this to copy the files from the old laptop's disk to the new one with similar VG names (I had used homevg as the name).
<hr />
