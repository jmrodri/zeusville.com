---
title: 'Fedora 13 *installed*'
date: Tue, 28 Sep 2010 19:22:51 +0000
draft: false
tags: [Linux, Technology]
categories: [Linux, Technology]
type: post
---

I finally got Fedora 13 installed after having some issues with my software RAID partition [last night.](http://zeusville.wordpress.com/2010/09/27/fedora-13-install-a-no-go/)

I have 3 250GB drives. Two of them were software raided in RAID 1 configuration holding `/home`. The third is where the OS lives. I ignored the error message anaconda presented me since I could still use `/dev/sda` which is where I wanted to install anyway.

I choose to **Fresh Install** from the menu, then **Basic Storage Devices**. I proceeded to choose the only hard drive that showed up, and said I'd create my own custom partition layout. This part probably wasn't necessary but I wanted to make sure the partitions that existed were the ones on `/dev/sda` :)

Once the installation was done, I switched to runlevel 3 and logged in as root. This is what I did to recover my software RAID partitions to mount them as `/home`.

```
\# mdadm --assemble --scan

# cat /prod/mdstat

Personalities : \[raid1\]

md0 : active raid1 sdc1\[1\] sdb1\[0\]

      244195904 blocks \[2/2\] \[UU\]

unused devices:

# mdadm --examine --scan >> /etc/mdadm.conf

# tail -n 1 /etc/mdadm.conf

ARRAY /dev/md0 UUID=93ea08fa:1a7ae881:f59ceb98:8b2b169f

So far so good. But `df -h` didn't show my LVM partition from the RAID device.

`lvscan` showed it as inactive:

```
\# lvscan

  ACTIVE            '/dev/vg0/lvswap' \[3.00 GiB\] inherit

  ACTIVE            '/dev/vg0/lvroot' \[214.69 GiB\] inherit

  inactive          '/dev/vg1/lvhome' \[232.88 GiB\] inherit

Ok simple need to change that.

```
\# vgchange -ay

  2 logical volume(s) in volume group "vg0" now active

  1 logical volume(s) in volume group "vg1" now active

# lvscan

  ACTIVE            '/dev/vg0/lvswap' \[3.00 GiB\] inherit

  ACTIVE            '/dev/vg0/lvroot' \[214.69 GiB\] inherit

  ACTIVE            '/dev/vg1/lvhome' \[232.88 GiB\] inherit

# ls /dev/mapper/

control  vg0-lvroot  vg0-lvswap  vg1-lvhome

Last thing to do is get `/etc/fstab` updated:

```
/dev/mapper/vg1-lvhome  /home                   ext4    defaults        1 1
```

And for good measure, blow away the old user home dir from the install, and mount

the homedir:

```
\# rm -rf /home/jmrodri

# mount /home

# df -h

Filesystem            Size  Used Avail Use% Mounted on

/dev/mapper/vg0-lvroot

                      212G  5.8G  195G   3% /

tmpfs                1005M     0 1005M   0% /dev/shm

/dev/sda2             190M   50M  131M  28% /boot

/dev/mapper/vg1-lvhome

                      230G   91G  128G  42% /home

Sweet back in business. Let's reboot and make sure everything's good.

Everything was good upon reboot except when logging in as jmrodri it couldn't find my homedir. I checked the permissions and they were fine. What could it be? ponder. run series of commands. google. ponder some more. google. SELinux! The new /home had the wrong SELinux context.

```
\# restorecon -R /home
```

There now we're good.


```
```
```
```