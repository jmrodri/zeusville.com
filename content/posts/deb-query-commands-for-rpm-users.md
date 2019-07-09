---
title: 'deb query commands for rpm users'
date: Sun, 08 Apr 2007 17:15:01 +0000
draft: false
tags: [Linux]
categories: [Linux]
type: post
---

I've learned quite a few rpm commands which I find useful for querying rpms on my Fedora/RHEL systems. Now with Ubuntu on my mom's machine I've found similar commands to work with deb pkgs.

There are many ways to query using rpm, but I'll show the ones I use most often.

List files in a package (not yet installed):

`rpm -qlp <pkgname>``dpkg -c <pkgname>`

List files in an **installed** package:

`rpm -ql <pkgname>``dpkg -L <pkgname>`

List all installed packages:

`rpm -qa``dpkg -l`