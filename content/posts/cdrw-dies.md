---
title: 'CDRW dies'
date: Sun, 30 May 2004 22:10:36 +0000
draft: false
tags: [Linux]
categories: [Linux]
type: post
---

Late last week, while using my [Yamaha CRW2100S (SCSI)](http://www.yamaha.co.jp/english/product/computer/products/crw2100/crw2100.html) drive, I started getting SCSI bus errors, like the following ones:

```
May 30 15:54:00 firebird kernel: Current sr: sense key Hardware Error
May 30 15:54:00 firebird kernel: Additional sense: Track following error
May 30 15:54:00 firebird kernel: sym0:3:0: ABORT operation started.
May 30 15:54:00 firebird kernel: sym0:3:0: ABORT operation failed.
May 30 15:54:00 firebird kernel: sym0:3:0: DEVICE RESET operation started.
May 30 15:54:00 firebird kernel: sym0:3:0: DEVICE RESET operation complete.
May 30 15:54:00 firebird kernel: sym0:3:control msgout: c.
May 30 15:54:00 firebird kernel: sym0: TARGET 3 has been reset. 

```Needless to say I was disappointed. Several [Google](http://www.google.com) searches for the above error pointed to two things:

1) SCSI bus termination problems  
2) Drive going bad

Having figured out the termination many months ago, I ruled that out. But just to make 100% sure, I opened up the case and checked to ensure nothing came loose. Every thing checked out ok. The external zip drive was terminated as was the internal 50-pin cable (with active terminator). The 68 pin side was terminated at the card and the active terminator at the end of the cable. The termination was ok.

After checking the termination I reboot the machine to see what else I can diagnose. Then,' "Hey what's that weird @$$ whining noise?" CRAP! CDRW spinning with no disc in it going at all speeds. ARGH! Sure enough the drive is toast.

Now my dilemna is that there aren't any good SCSI CDRW's out there anymore. I looked on [eBay](http://www.ebay.com) and no one's selling a used 2100S or 2200S. This is starting to sound like I'll need a new IDE drive which I dread because I became a SCSI ho several years ago.

I'll continue my quest for a SCSI CDRW or just bite the bullet and get a kick @$$ DVDRW :)

Here are a few I'd consider buying:

[Sony DRU-700A](http://www.sonystyle.com/is-bin/INTERSHOP.enfinity/eCS/Store/en/-/USD/SY_DisplayProductInformation-Start;sid=1pzi9sEOkurirIG0R2vo_Y4fIJXeyk1SvpI=?CategoryName=cpu_Sony_PCAccessories_CD%2fDVDBurn_DVDBurners&ProductSKU=DRU700A&Dept=cpu)  
[Plextor PX-708A](http://www.plextor.com/english/products/708a.html)  
[Plextor PX-712A](http://www.plextor.com/english/products/712a.htm)

If I had my P4 machine with SATA, I'd just ditch the SCSI drives and get all new SATA drives.

Oh well, C'est la vie!