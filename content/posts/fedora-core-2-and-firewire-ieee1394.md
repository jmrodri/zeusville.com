---
title: 'Fedora Core 2 and Firewire (IEEE1394)'
date: Tue, 06 Jul 2004 09:54:37 +0000
draft: false
tags: [Linux]
categories: [Linux]
type: post
---

After [reinstalling](/20040704) Fedora Core 2, I updated it with the latest kernel [(2.6.6-1.435.2.3).](http://download.fedora.redhat.com/pub/fedora/linux/core/updates/2/i386/kernel-2.6.6-1.435.2.3.i686.rpm) I was hoping it would autodetect my firewire card now that the [fix](http://www.ic.unicamp.br/%7Eoliva/snapshots/FC2-firewire/0README) was in. But upon reboot, nothing changed. I did several googles and then gave the following a try:```
/sbin/modprobe ohci1394
/sbin/modprobe sbp2
/sbin/modprobe raw1394

```This resulted in```
Jul  5 14:20:41 machinename kernel: ohci1394: fw-host0: \\
OHCI-1394 1.1 (PCI): IRQ=\[10\]  MMIO=\[f1109000-f11097ff\] \\
Max Packet=\[2048\]

```The firewire card is recognized now. Now I'm trying to attempt to mount my [iPod](http://www.apple.com/ipod). Every article I found on the net said it will be recognized as /dev/sda1 or /dev/sda2. My problem is that I already have a /dev/sda and /dev/sdb since I've got a SCSI system.

I'll keep looking more this week on getting this to work. My ultimate goal is to get the an external Firewire/USB drive to work for backup purposes.