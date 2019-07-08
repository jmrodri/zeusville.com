---
title: 'Google yum repos'
date: Sat, 25 Aug 2007 17:14:03 +0000
draft: false
tags: [Linux]
type: post
---

Here's an easy way to install [Google](http://www.google.com) software on [Fedora](http://http://fedoraproject.org/wiki/) by using their [yum repo](http://www.google.com/linuxrepositories/yum.html). Put the following in /etc/yum.repo.d/google.repo `[google] name=Google - i386 baseurl=http://dl.google.com/linux/rpm/stable/i386 enabled=1 gpgcheck=1` If you're not a [Fedora](http://http://fedoraproject.org/wiki/) user (though you should be), [Google](http://www.google.com) has other repositories as well: [http://www.google.com/linuxrepositories/index.html](http://www.google.com/linuxrepositories/index.html)