---
title: 'Linux Tip: Scanner not found?'
date: Mon, 31 May 2004 00:39:17 +0000
draft: false
tags: [Linux]
categories: [Linux]
type: post
---

After upgrading to [Fedora Core 2](http://fedora.redhat.com), I've been generally happy with it. I decided to give my HP ScanJet 5p SCSI scanner a shot. I start GIMP 2.0 (nice by the way), and choose "Acquire -> XSane: Device dialog...". The result is "no devices available".

![](http://jroller.com/resources/jmrodri/xsane_no_dev.png)

ARGH! This is yet another issue with Linux compared with Windows. Linux recognizes my scanner since it it is displayed by dmesg.

```


  Vendor: HP        Model: C5110A            Rev: 3638

  Type:   Processor                          ANSI SCSI revision: 02

This is odd.  So I run xsane from the command line and still the same result. Su to root and run xsane, it finds my scanner.  Bingo!  Permisions problem.  I do:

```


chmod 666 /dev/sg0

Restart GIMP, and viola, I can scan.  Again, from a user's point of view, I shouldn't have to do this.  It should be automatic or during installation I should be asked "Allow non-root to use scanner?"  Personally everyone should be able to use the scanner, so it should've been setup correctly by default.


```
```