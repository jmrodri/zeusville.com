---
title: 'Fedora 13 battery icon is wrong'
date: Thu, 20 May 2010 01:30:55 +0000
draft: false
tags: [Linux, Technology]
---


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
