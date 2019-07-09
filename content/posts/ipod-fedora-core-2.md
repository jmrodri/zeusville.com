---
title: 'iPod & Fedora Core 2'
date: Fri, 09 Jul 2004 15:18:03 +0000
draft: false
tags: [Linux]
categories: [Linux]
type: post
---

**I DID IT! I DID IT!** I got my iPod and Fedora Core 2 talking to each other. It was an uphill battle.

Apparently, FC2 was shipped with firewire turned off:

> Fedora Core 2 ships with a kernel that's quite close to 2.6.6 and
> 
> that, as such, has seriously broken Firewire modules, so they were
> 
> disabled to avoid the problems described in section 0.1.
> 
> [link](http://www.ic.unicamp.br/%7Eoliva/snapshots/FC2-firewire/0README)

Here's what I did to get the iPod to work with FC2.

### Hardware

Belkin 3-port FireWire PCI card Model:

[F5U503](http://catalog.belkin.com/IWCatProductPage.process?Merchant_Id=&Section_Id=1969&pcount=&Product_Id=149022)

Apple [iPod](http://www.apple.com/ipod/index.html) 20GB

![](http://jroller.com/resources/jmrodri/ipod.jpg)

### Configuration

Edited my /etc/modprobe.conf:

```


alias ieee1394-controller ohci1394

alias scsi\_hostadapter1 sbp2

\*NOTE: scsi\_hostadapter1 was added since I already have an LSI Logic scsi adapter.

Kuzdu added the following to /etc/fstab:

```


/dev/sdc2  /mnt/ipod  auto  noauto,owner,kudzu 0 0

### Log messages

If you connect your iPod after Linux has booted you might see the following errors in /var/log/messages file:

```


ieee1394.agent\[3185\]: ... no drivers for IEEE1394 product 0x/0x/0x

Googling for the above error yielded an article stating the following (see resources below):

>  I haven't really sorted out the problem but I have noticed that is the
> 
> ipod is picked up and mounted if the ipod is plugged in when the machine
> 
> is booted.

Connect your iPod, reboot into Linux and kudzu should kick in asking if you want to configure new device called "iPo".  Click on configure.  Then in your /var/log/messages file should be the following (sdc might be sda if you don't have any other SCSI devices):

```


kernel: scsi2 : SCSI emulation for IEEE-1394 SBP-2 Devices

kernel: ieee1394: sbp2: Logged into SBP-2 device

kernel:  Vendor: Apple     Model: iPod Rev: 1.51

kernel:  Type:   Direct-Access         ANSI SCSI revision: 02

### On the filesystem

Kudzu should've created /mnt/ipod for you, if not create it. Then mount /mnt/ipod.  Doing an ls -l /mnt/ipod yields four directories: Calendars, Contacts, iPod\_Control, and Notes.  Your music is located in a series of directories fXX where XX is a 2 digit number,  on my iPod it's 00 - 49.  Those fXX directories are located in /mnt/ipod/iPod\_Control/Music.

![](http://fedora.redhat.com/images/header-fedora_logo.png)

Most of the above was trial and error with many reboots in between.  [FC3](http://fedora.redhat.com/participate/schedule/) should be out next week and it should have the FireWire built in to the kernel already during installation.

### Resources

[kernel-2.6.6-1.435.2.3](http://fedoranews.org/updates/FEDORA-2004-205.shtml)

[iPod not recognized](http://www.linux.ie/pipermail/ilug/2004-June/016218.html)

[Linux 1394 site](http://www.linux1394.org/)

[RIMBoy's Firewire Storage How-to](http://www.rimboy.com/firewire/#dh)


```
```
```
```