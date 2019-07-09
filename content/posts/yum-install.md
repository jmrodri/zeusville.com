---
title: 'yum install ...'
date: Tue, 10 Apr 2007 16:31:02 +0000
draft: false
tags: [Linux]
categories: [Linux]
type: post
---

I swear I learn something new everyday. :) I reinstalled [Fedora Core 6](http://fedoraproject.org/wiki/) on my workstation today, and went to reinstall [mugshot](http://mugshot.org/main).

I downloaded the mugshot client, and attempted to install it:

`sudo rpm -Uvh mugshot-1.1.40-1.fc6.x86_64.rpm`

But it failed missing some dependencies:

`error: Failed dependencies:`

`libloudmouth-1.so.0()(64bit) is needed by mugshot-1.1.40-1.fc6.x86_64`

`loudmouth >= 1.0.3-3 is needed by mugshot-1.1.40-1.fc6.x86_64`

I quickly griped that I wish there was a yum repo with mugshot in it. !@#$%^

Then the light went on in my feable brain. I wonder if `yum install path/to/rpm` will work? Only one way to find out.

`yum install ~/downloads/mugshot-1.1.40-1.fc6.x86_64.rpm`

WOO HOO, I worked. Yum properly processed the dependencies and sucked them down from the my currently subscribed yum repos.

```


Dependencies Resolved

=============================================================================

 Package                 Arch       Version          Repository        Size

=============================================================================

Installing:

 mugshot                 x86\_64     1.1.40-1.fc6     /home/devel/jesusr/ftp/mugshot-1.1.40-1.fc6.x86\_64.rpm  811 k

Installing for dependencies:

 loudmouth               x86\_64     1.0.5-2.fc6      extras             53 k

That was cool!


```