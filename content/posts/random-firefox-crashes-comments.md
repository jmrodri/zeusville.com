---
title: 'random firefox crashes'
date: Mon, 10 Mar 2008 23:57:24 +0000
draft: false
tags: [Linux]
---


#### 
[darrell]( "darrellpf@gmail.com") - <time datetime="2008-03-10 20:46:47">Mar 1, 2008</time>

https://bugzilla.redhat.com/show\_bug.cgi?id=428537
<hr />
#### 
[Dark Falcon]( "spam@choseones.dyndns.org") - <time datetime="2008-03-15 20:47:03">Mar 6, 2008</time>

I had this problem and found that my sound devices in /dev had inappropriate permissions. Sound worked fine logging in as root. I added a couple udev rules to force the correct permissions.
<hr />
