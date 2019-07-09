---
title: 'just update already'
date: Tue, 02 Jun 2009 12:05:22 +0000
draft: false
tags: [Linux, Technology]
categories: [Linux, Technology]
type: post
---

I've grown tired of these stupid 'waiting' messages. Time to find a remedy.

```


$ sudo yum list updates

Loaded plugins: allowdowngrade, changelog, fastestmirror, priorities, refresh-

              : packagekit

Existing lock /var/run/yum.pid: another copy is running as pid 7292.

Another app is currently holding the yum lock; waiting for it to exit...

Another app is currently holding the yum lock; waiting for it to exit...

Another app is currently holding the yum lock; waiting for it to exit...

Another app is currently holding the yum lock; waiting for it to exit...

Another app is currently holding the yum lock; waiting for it to exit...

Another app is currently holding the yum lock; waiting for it to exit...

Another app is currently holding the yum lock; waiting for it to exit...

Another app is currently holding the yum lock; waiting for it to exit...

Another app is currently holding the yum lock; waiting for it to exit...

Another app is currently holding the yum lock; waiting for it to exit...

Another app is currently holding the yum lock; waiting for it to exit...

Another app is currently holding the yum lock; waiting for it to exit...

yum-updatesd you are dead to me now. This is the last time you bother poor little yum :)

```


$ sudo kill 7292

$ sudo yum remove yum-updatesd

...

Removed:

  yum-updatesd.noarch 1:0.9-1.fc9                                                    

Complete!


```
```
---
### Comments:
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
