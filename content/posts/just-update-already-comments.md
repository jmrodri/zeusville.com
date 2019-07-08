---
title: 'just update already'
date: Tue, 02 Jun 2009 12:05:22 +0000
draft: false
tags: [Linux, Technology]
---


#### 
[pdusen]( "patrick@pdusen.com") - <time datetime="2009-06-02 12:50:21">Jun 2, 2009</time>

@bochecha: yum-updatesd has been present on every Fedora 10 install I have done.
<hr />
#### 
[Rahul Sundaram]( "sundaram@fedoraproject.org") - <time datetime="2009-06-02 16:50:48">Jun 2, 2009</time>

" @bochecha: yum-updatesd has been present on every Fedora 10 install I have done. " Comps doesn't indicate it being installed by default.
<hr />
#### 
[Max]( "mspevack@redhat.com") - <time datetime="2009-06-02 08:53:13">Jun 2, 2009</time>

That is the first thing I do after an install.
<hr />
#### 
[red](http://sandro-mathys.ch/ "red@fedoraproject.org") - <time datetime="2009-06-02 09:53:11">Jun 2, 2009</time>

FYI: AFAIK this issue was fixed for F11 :)
<hr />
#### 
[bochecha](http://blog.fedora-fr.org/bochecha "bochecha@fedoraproject.org") - <time datetime="2009-06-02 12:37:06">Jun 2, 2009</time>

Wait, yum-updatesd ? Wasn't it replaced by the PackageKit daemon ? I think I haven't heard of yum-updatesd on my system since Fedora 10, it wasn't installed by default here... Also, the yum messages are quite different with latest versions... Are you stil on Fedora 9 ? If so, you might really want to upgrade. PackageKit works in a different way. You don't have a daemon blocking you for such a long time. And when it does block you (usually just after a previous yum operation), it does so for a very short time.
<hr />
