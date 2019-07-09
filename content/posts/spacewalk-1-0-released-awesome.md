---
title: 'Spacewalk 1.0 RELEASED! AWESOME!'
date: Fri, 30 Apr 2010 13:41:53 +0000
draft: false
tags: [Linux, spacewalk, Technology]
categories: [Linux, spacewalk, Technology]
type: post
---

Almost two years ago, I was involved in the [open sourcing](https://www.redhat.com/archives/spacewalk-list/2008-June/msg00000.html) effort of Spacewalk. While I've moved on to other [projects](https://fedorahosted.org/candlepin/) since then, [Spacewalk](https://fedorahosted.org/spacewalk/) still holds a special place in my heart.

Yesterday the Spacewalk team announced the release of version 1.0! This is an exciting milestone. Here's a summary of some of the things you'll find in 1.0.

![](https://fedorahosted.org/spacewalk/attachment/wiki/WikiStart/spacewalk-1-0-release.png?format=raw)

**Features & Enhancements**

*   RHN Client code dropped HAL in favor of python-ugdev

*   New script to rename Spacewalk hostname

*   RHN Proxy migrated to mod\_wsgi

*   The Spacewalk java stack uses Tomcat 6 on Fedora 12

**Known Issues**

*   Provider GPG key is sometimes not recognized causing packages to show up as 'unknown Provider'

*   Still no PostgreSQL support. We need _**HELP**_ to move this forward.

Checkout the [OFFICIAL announcement: here.](https://www.redhat.com/archives/spacewalk-announce-list/2010-April/msg00000.html)

Congrats to the Spacewalk team for reaching this important milestone.
---
### Comments:
####
[neverho0d](http://www.abbris.ru "psv@abbris.ru") - <time datetime="2010-05-03 10:57:44">May 1, 2010</time>

I think, it shouldn't reach 1.0 without PostgreSQL support. Open source solution can not rely on proprietary one. Shit happens. :(
<hr />
####
[isimluk]( "isimluk@fedoraproject.org") - <time datetime="2010-04-30 16:08:41">Apr 5, 2010</time>

s/python-ugdev/python-gudev
<hr />
