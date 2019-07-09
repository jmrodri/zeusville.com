---
title: 'Leonidas broke suspend'
date: Thu, 09 Jul 2009 00:21:31 +0000
draft: false
tags: [Linux]
categories: [Linux]
type: post
---

Fedora 11 has broken my suspend :( It worked find in Fedora 8/9/10. Sigh, time to figure out what the heck is going on.

```
WARNING: at kernel/hrtimer.c:625 hres\_timers\_resume+0x34/0x4a() (Not tainted)

Hardware name: 2687D7U

hres\_timers\_resume() called with IRQs enabled!Modules linked in: arc4 ecb lib80211\_crypt\_wep fuse sco bridge stp llc bnep l2cap bluetooth sunrpc ip6t\_REJECT nf\_conntrack\_ipv6 ip6table\_filter ip6\_tables ipv6 cpufreq\_ondemand acpi\_cpufreq dm\_multipath uinput ppdev snd\_intel8x0m snd\_intel8x0 snd\_ac97\_codec ac97\_bus snd\_pcm thinkpad\_acpi ipw2200 snd\_timer nsc\_ircc parport\_pc snd iTCO\_wdt libipw irda iTCO\_vendor\_support hwmon yenta\_socket parport i2c\_i801 video soundcore lib80211 pcspkr tg3 snd\_page\_alloc output rsrc\_nonstatic joydev crc\_ccitt ata\_generic pata\_acpi xts gf128mul aes\_i586 aes\_generic dm\_crypt radeon drm i2c\_algo\_bit i2c\_core \[last unloaded: scsi\_wait\_scan\]

Pid: 2724, comm: pm-suspend Not tainted 2.6.29.5-191.fc11.i686.PAE #1

Call Trace:

\[\] warn\_slowpath+0x7c/0xa4

\[\] ? ktime\_get\_ts+0x4f/0x53

\[\] ? lapic\_next\_event+0x18/0x1c

\[\] ? clockevents\_program\_event+0xe1/0xf0

\[\] ? tick\_dev\_program\_event+0x47/0xb5

\[\] ? tick\_program\_event+0x26/0x2e

\[\] ? tick\_notify+0x2e8/0x2f7

\[\] ? hpet\_resume\_counter+0x0/0x51

\[\] ? notifier\_call\_chain+0x26/0x48

\[\] hres\_timers\_resume+0x34/0x4a

\[\] timekeeping\_resume+0x130/0x138

\[\] \_\_sysdev\_resume+0x19/0x3d

\[\] sysdev\_resume+0x26/0x59

\[\] suspend\_devices\_and\_enter+0x112/0x186

\[\] enter\_state+0x142/0x19d

\[\] state\_store+0x98/0xac

\[\] ? state\_store+0x0/0xac

\[\] kobj\_attr\_store+0x16/0x22

\[\] sysfs\_write\_file+0xc9/0xf4

\[\] ? sysfs\_write\_file+0x0/0xf4

\[\] vfs\_write+0x95/0xf4

\[\] sys\_write+0x4c/0x70

\[\] sysenter\_do\_call+0x12/0x34

---\[ end trace 98ea38b8c74f376f \]---


```
---
### Comments:
#### 
[Hub](http://www.figuiere.net/hub/blog/ "hub@figuiere.net") - <time datetime="2009-07-08 21:07:42">Jul 3, 2009</time>

What about cc'ing yourself to this bug? https://bugzilla.redhat.com/show\_bug.cgi?id=499651
<hr />
