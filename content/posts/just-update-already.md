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