---
title: 'Fedora 13 install a no go'
date: Tue, 28 Sep 2010 00:45:14 +0000
draft: false
tags: [Linux, Technology]
categories: [Linux, Technology]
type: post
---

Tonight I tried to install Fedora 13 over my old Fedora 11. The plan was to use /dev/sda1 as / and keep /home on my software raid RAID1 partition (/dev/sdb1 and /dev/sdc1). But during the install I got an error message:

```
                 Warning

Disks sdb, sdc contain BIOS RAID metadata, but are not

part of any recognized BIOS RAID sets. Ignorning disks sdb,

sdc.

So I went through all of the CTRL-ALT-F{1-6} to gather information.

**CTRL-ALT-F1**

```
Running anaconda 13.42, the Fedora system installer - please wait.

00:20:36 Starting graphical installation.

ERROR: sil: RAID tyep 253 not supported

ERROR: adding /dev/sdc to RAID set "sil\_aiaicadebade"

ERROR: sil: RAID tyep 253 not supported

ERROR: adding /dev/sdb to RAID set "sil\_aiaicadebade"

ERROR: no RAID set found

**CTRL-ALT-F2**

```
tail storage.log shows:

DEBUG storage: registered device format class LVMPhysicalVolume as lvmpv

DEBUG storage: registered device format class MDRaidMember as mdmember

DEBUG storage: registered device format class MultipathMember as multipath\_member

DEBUG storage: registered device format class PPCPRePBoot as prepboot

DEBUG storage: registered device format class SwapSpace as swap

INFO storage: devices to scan for multipath: \['sda', 'sdb', 'sdc'\]

INFO storage: adding sda to singlepath\_disks

INFO storage: adding sdb to singlepath\_disks

INFO storage: adding sdc to singlepath\_disks

INFO storage: devices post multipath scan: (\['sda', 'sdb', 'sdc'\], \[\], \[\])

fdisk -l shows:

Disk /dev/sda: 250.1 GB, 250... bytes

...

Device Boot    Start    End    Blocks  Id  System

/dev/sda1          1   1958             7  HPFS/NTFS

/dev/sda2       1959   1984            83  Linux

/dev/sda3       1984  30401            8e  Linux LVM

Disk /dev/sdb: 250.1 GB, 250... bytes

...

Device Boot    Start    End    Blocks  Id  System

/dev/sdb1          1  30401            fd  Linux raid autodetect

Disk /dev/sdc: 250.1 GB, 250... bytes

...

Device Boot    Start    End    Blocks  Id  System

/dev/sdc1          1  30401            fd  Linux raid autodetect

**CTRL-ALT-F3**

last 5 lines show

```
INFO storage: devices to scan for multipath: \['sda', 'sdb', 'sdc'\]

INFO storage: adding sda to singlepath\_disks

INFO storage: adding sdb to singlepath\_disks

INFO storage: adding sdc to singlepath\_disks

INFO storage: devices post multipath scan: (\['sda', 'sdb', 'sdc'\], \[\], \[\])

**CTRL-ALT-F4**

```
DEBUG kernel:SELinux: ....

NOTICE kernel:tyep=1403 audit(1285633217.220;2): policy loaded auid=4294967295 ses=4294967295

INFO kernel:md: raid0 personality registered for level 0

INFO kernel:md: raid1 personality registered for level 1

INFO kernel:async\_tx: api intialized (async)

INFO kernel:xor: automatically using best checksumming function: generic\_sse

...

WARN kernel:raid6: int64x1  2117 MB/s

WARN kernel:raid6: int64x2  2378 MB/s

WARN kernel:raid6: int64x4  1835 MB/s

WARN kernel:raid6: int64x8  1371 MB/s

WARN kernel:raid6: sse2x1   2429 MB/s

WARN kernel:raid6: sse2x2   3335 MB/s

WARN kernel:raid6: sse2x4   3812 MB/s

INFO kernel:md: raid6 personality registered for level 6

INFO kernel:md: raid5 personality registered for level 5

INFO kernel:md: raid4 personality registered for level 4

INFO kernel:md: raid10 personality registered for level 10

INFO kernel:md: linear personality registered for level -1

Anyone have any thoughts? This setup works fine in Fedora 11. How can I get past this error so I can mount /home on my software raid partitions.


```
```
```
```
```
---
### Comments:
####
[Bucky]( "bucky@mightytikigod.com") - <time datetime="2010-09-27 21:46:06">Sep 1, 2010</time>

I haven't had this problem in Fedora (I haven't created software RAID partitions with Fedora), but the Anaconda in CentOS (in my experience) has problems mounting previously-created software RAID volumes. Verify that you can boot into Rescue mode of the Fedora 13 installer and use the mdadm command to assemble your RAID (if it's like CentOS, it will fail to do it automatically, but succeed if you generate an /etc/mdadm.conf file and run the commands yourself). If this works, then just do a regular install and carefully avoid touching the partitions which constitute your /home RAID. When you reboot into Fedora 13, reassemble your RAID with mdadm, regenerate /etc/mdadm.conf and edit /etc/fstab by hand.
<hr />
####
[amachina]( "amachina@cavtel.net") - <time datetime="2011-03-15 21:31:07">Mar 2, 2011</time>

I experienced the same problem. What finally worked for me is: 1) boot into rescue mode 2) execute dd if=/dev/zero of=/dev/sda
<hr />
