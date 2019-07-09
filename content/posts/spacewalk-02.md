---
title: 'Spacewalk 0.2!'
date: Tue, 16 Sep 2008 20:33:18 +0000
draft: false
tags: [Linux]
categories: [Linux]
type: post
---

The [Spacewalk](http://spacewalk.redhat.com) team is proud to announce the release of Spacewalk 0.2. In a few hours, the repos will be accessible and you can install 0.2 and try it out.

[![](/img/2008/09/spacewalk-release.png "Spacewalk 0.2 Release")](http://spacewalk.redhat.com)

**Features & Enhancements**

*   new APIs, primarily in the kickstart. namespace

*   an enhanced errata search

*   fully support multiple distributions within a single org: [Red Hat Enterprise Linux](http://www.redhat.com/rhel/), [Fedora](http://fedoraproject.org/get-fedora), [CentOS](http://www.centos.org/)

*   more perl to java migrations (mostly in the Channel management area)

*   re-spun all packages in a new koji build system

*   new versioned repos, the idea is to keep the current and the previous releases available, see the wiki for the new locations: [https://hosted.fedoraproject.org/spacewalk/wiki/HowToInstall#Installation](https://hosted.fedoraproject.org/spacewalk/wiki/HowToInstall#Installation)

**Bugs fixed**

*   Fixed 500 error when creating custom channels

*   Fixed some x86\_64 Oracle errors with oracle-lib-compat package

*   Fixed IllegalStateException (StopWatch error) while accessing API

*   [38 total bugs](http://tinyurl.com/6aqqpk) fixed since 0.1

**Known issues**

*   upgrading from 0.1 to 0.2 will be available soon

*   monitoring is borked in 0.2 release

*   Spacewalk running on Fedora moved to 0.3

**Community**

*   Kudos to Rob James, Steve Milner, and particularly, Colin Coe for their

    contributions to this release, see the [contributors list](https://hosted.fedoraproject.org/spacewalk/wiki/ContibutorList).
---
### Comments:
####
[snerd](http://motk.blogspot.com "robk@ningaui.net") - <time datetime="2008-09-16 18:55:38">Sep 2, 2008</time>

Good stuff. I'm interested in the medium to long term plans for spacewalk and it's relationship to cobbler/koan. Is there a venn-diagram yet? :)
<hr />
####
[Michael DeHaan](http://michaeldehaan.net/ "michael.dehaan@gmail.com") - <time datetime="2008-09-16 19:47:16">Sep 2, 2008</time>

Snerd, The current plan is for Spacewalk to utilize Cobbler/Koan for provisioning/installation as the engine for the "5.3" release for Satellite, and zeus can tell you what Spacewalk release that is. Cobbler remains seperately usable and available for those who want it, this is very much the continued idea of having "Voltronic Software" -- writing tools that can be used by multiple larger projects but also seperately. Satellite is one such robot, oVirt is another, genome is a third example, what others develop in house could be called a fourth. There is no Venn Diagram as they cause painful flashbacks to 3rd grade, but if there was, the Spacewalk circle surrounds the cobbler circle at least part way, and there are some features in cobbler that Spacewalk probably won't leverage (for example, VMware support). Things like DHCP and DNS management should be in though, as well as all the templating bits. What actually powers repo mirroring in the future Spacewalk is still TBD.
<hr />
####
[Devan](http://dgoodwin.dangerouslyinc.com "dgoodwin@dangerouslyinc.com") - <time datetime="2008-09-16 22:18:10">Sep 2, 2008</time>

Woooooo wooo!
<hr />
