---
title: 'building rpms without being root'
date: Thu, 07 Dec 2006 13:46:53 +0000
draft: false
tags: [Linux]
categories: [Linux]
type: post
---

I got tired of having to become root to install a src.rpm and to build it. Turns out a little magic in `$HOME/.rpmmacros` will do the trick. Do the following:

`mkdir -p $HOME/rpmbuild/{BUILD,RPMS,SOURCES,SPECS,SRPMS}`

`echo "%home %(echo $HOME)" >> $HOME/.rpmmacros`

`echo "%_topdir %{home}/rpmbuild" >> $HOME/.rpmmacros`

Now when you install a src.rpm it will go to `$HOME/rpmbuild/` instead of `/usr/src/redhat/`.

That's it.