---
title: 'banshee and older iPods'
date: Fri, 17 Jul 2009 01:13:03 +0000
draft: false
tags: [Linux, Technology]
categories: [Linux, Technology]
type: post
---

With the release of [banshee](http://banshee-project.org/) 1.0, podsleuth was re-written to work with later models of iPods but ended up breaking compatibility with 3rd gen iPods (like mine). I tried creating a patch but C# is not my forte and time was lacking as well.

But today I found that a patch was committed that fixes [bug #486661](http://bugzilla.gnome.org/show_bug.cgi?id=486661): commit [8c17bbb6e3fa9bd39c4c43c0e28a30a6795a189c](http://git.gnome.org/cgit/podsleuth/commit/?id=8c17bbb6e3fa9bd39c4c43c0e28a30a6795a189c) in podsleuth.

I downloaded the F9 src.rpm from [koji](http://koji.fedoraproject.org/koji/buildinfo?buildID=69124) and created a patch from the above mentioned commit. I rebuilt the rpm and installed it on my Fedora 9 x86\_64 machine. I'm happy to say I'm back in business!

`[jmrodri@firebird podsleuth]$ rpm -qa 'podsleuth*'`

`podsleuth-0.6.4-2.zeus.fc9.x86_64`

`podsleuth-devel-0.6.4-2.zeus.fc9.x86_64`

Thanks to Nicolas Cortot for submitting the patch, and to [Gabriel Burt](http://gburt.blogspot.com/) for applying the patch.

[![banshee-ipod](/img/2009/07/banshee-ipod.png "banshee-ipod")](/img/2009/07/banshee-ipod.png)