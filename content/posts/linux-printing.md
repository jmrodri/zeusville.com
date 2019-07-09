---
title: 'Linux printing :('
date: Tue, 03 Apr 2007 01:51:33 +0000
draft: false
tags: [Linux]
categories: [Linux]
type: post
---

Like I stated [earlier,](http://zeusville.wordpress.com/2007/04/01/this-weekend/) I got Ubuntu setup on my mom's new Dell laptop. Today the printer arrived, I bought a Canon [PIXMA ip6310D](http://www.newegg.com/Product/Product.aspx?Item=N82E16828102033). It met my mom's price criteria, and I have a Canon S750 working ok at home. Well, this is where Linux fails the hardest. :(

I thought the fact that it was a USB printer would be a problem. But Linux recognized it immediately:

`Apr 2 19:58:04 luisa kernel: [128078.504000] usb 6-3: new high speed USB device using ehci_hcd and address 8`

`Apr 2 19:58:04 luisa kernel: [128078.636000] usb 6-3: configuration #1 chosen from 1 choice`

`Apr 2 19:58:04 luisa kernel: [128078.640000] drivers/usb/class/usblp.c: usblp0: USB Bidirectional printer dev 8 if 0 alt 0 proto 2 vid 0x04A9 pid 0x10BA`

`Apr 2 19:58:04 luisa kernel: [128078.640000] scsi5 : SCSI emulation for USB Mass Storage devices`

`Apr 2 19:58:04 luisa kernel: [128078.644000] hiddev96: USB HID v1.10 Device [Canon iP6310D] on usb-0000:00:13.5-3`

`Apr 2 19:58:09 luisa kernel: [128083.640000] scsi 5:0:0:0: Direct-Access Canon iP6310DStorage 0103 PQ: 0 ANSI: 2`

`Apr 2 19:58:09 luisa kernel: [128083.648000] sd 5:0:0:0: Attached scsi removable disk sdb`

`Apr 2 19:58:09 luisa kernel: [128083.648000] sd 5:0:0:0: Attached scsi generic sg1 type 0`

[![print dialog](http://zeusville.files.wordpress.com/2007/04/ubuntu_canonprinter.png)](http://zeusville.files.wordpress.com/2007/04/ubuntu_canonprinter.png "print dialog")

But when I went to select a driver, there wasn't one. I tried a few of the ones from the list but none would print anything out :( I then tried [TurboPrint](http://www.turboprint.info/) drivers but couldn't find one for the [ip6310D](http://www.turboprint.info/printers.html). I tried the 6210 driver, and it actually printed the test page ok. Though there's no way to see if it will use all of the capabilities of the printer without buying it. If I can get a decent photo print from the TurboPrint drivers, I might be able to stick with Linux and avoid the whole virus infestation that is Windoze. I'll keep everyone posted on my progress.