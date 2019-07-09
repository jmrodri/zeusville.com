---
title: 'Fedora 13 battery icon is wrong'
date: Thu, 20 May 2010 01:30:55 +0000
draft: false
tags: [Linux, Technology]
categories: [Linux, Technology]
type: post
---

I've been running Fedora 13 beta on my laptop for quite a while. But I haven't been able to figure out what causes this scenario. It happens after a suspend/resume cycle. The battery popup clearly shows 7 hours + remaining, but the percentage and the icon are completely wrong.

[![](http://zeusville.files.wordpress.com/2010/05/battery.png "battery")](http://zeusville.files.wordpress.com/2010/05/battery.png)

Running acpi yields more accurate information:

```
\[jesusr@speed3 ~\]$ acpi -b

Battery 0: Discharging, 81%, 06:25:37 remaining

and acpitool shows the following:

```


\[jesusr@speed3 ~\]$ acpitool -B

  Battery #1     : present

    Remaining capacity : 7479 mAh, 81.01%, 07:09:00

    Design capacity    : 9324 mAh

    Last full capacity : 9232 mAh, 99.01% of design capacity

    Capacity loss      : 0.9867%

    Present rate       : 1046 mA

    Charging state     : discharging

    Battery type       : rechargeable 

    Model number       : 42T4799

    Serial number      :  6034

Could it be we have the decimal point in the wrong place? Seems like it should be 82% in the screenshot instead of 8.2%. Has this bug been fixed? If not, what package should I file the bug against? If you need a test user I'll be happy to test it :)


```
```
---
### Comments:
#### 
[jmrodri](http://zeusville.wordpress.com/ "jmrodri@gmail.com") - <time datetime="2010-05-20 08:51:55">May 4, 2010</time>

I updated last night and a new upower-0.9.4 package came in for Fedora 13. I have not been able to recreate the problem since then. Looking at the changelog, I think the problem was addressed: http://koji.fedoraproject.org/koji/buildinfo?buildID=173145 YAY!
<hr />
#### 
[bochecha](http://bochecha.fedorapeople.org "bochecha@fedoraproject.org") - <time datetime="2010-05-20 05:17:20">May 4, 2010</time>

\> "If not, what package should I file the bug against?" I'd say just report it against gnome-power-manager. It makes sens as it is the comonent handling the UI that appears to be wrong. Worst case, it will be a bug in something lower in the stack, and it will take around 10 minutes from the developer's time to reassign the bug ;)
<hr />
#### 
[Adam Williamson](http://www.happyassassin.net "awilliam@redhat.com") - <time datetime="2010-05-20 08:19:16">May 4, 2010</time>

I suspect the bug's probably in upower (which is what gnome-power-manager gets its info from, not from acpid directly).
<hr />
