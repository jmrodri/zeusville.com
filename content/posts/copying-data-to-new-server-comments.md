---
title: 'copying data to new server'
date: Fri, 04 Jun 2010 18:23:10 +0000
draft: false
tags: [Linux, Technology]
---


#### 
[Gigi]( "sgireeshmail@gmail.com") - <time datetime="2010-06-09 22:10:40">Jun 3, 2010</time>

Even if you had used the default VolGroup00, atleast on the latest fedora, vgdisplay will throw an error that "multiple vgs have the same name, so varying the one the one that was created on this machine". As long as the VGids are different, you can rename the one on the moved disk and import it. After my old laptop borked, I did this to copy the files from the old laptop's disk to the new one with similar VG names (I had used homevg as the name).
<hr />
