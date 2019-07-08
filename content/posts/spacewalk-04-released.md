---
title: 'Spacewalk 0.4 RELEASED!'
date: Fri, 16 Jan 2009 00:54:46 +0000
draft: false
tags: [Java, Linux, spacewalk]
type: post
---

Today we released [Spacewalk](https://fedorahosted.org/spacewalk/wiki/WikiStart) 0.4! It was an amazing release, I'm proud of the teams accomplishments with this release. We continue to move towards integrating open source projects as well as trying to get ourselves working on Fedora. Here are a few of what you will find in Spacewalk 0.4. **Features & Enhancements**

*   integration with [Cobbler](https://fedorahosted.org/cobbler/) and [Koan](http://git.fedoraproject.org/git/koan)
*   introduction Organization Trusts and Channel sharing, known internally as Multi-Org II: The Sequel.
*   [multi-arch enhancement](https://fedorahosted.org/spacewalk/wiki/MultiArchEnhancements) to better work with multi-arch packages on 64-bit systems.
*   a new set of [APIs](https://fedorahosted.org/spacewalk/wiki/ApiAdditions), including the following namespaces:
    *   channel.access.\*
    *   channel.org.\*
    *   package.\*
*   [SELinux](https://fedorahosted.org/spacewalk/wiki/Features/SELinux) support added
*   added the ability to search documentation, in Spacewalk we include a search index of the online docs.
*   updated the help page to include api docs and docs search
*   more perl to java migrations
*   satellite-httpd was removed in favor of using the standard httpd
*   upgrades from 0.3 -> 0.4 available as well: [https://fedorahosted.org/spacewalk/wiki/HowToUpgrade](https://fedorahosted.org/spacewalk/wiki/HowToUpgrade)

**Bugs fixed** An outstanding **118**! total bugs fixed since 0.3 - [http://tinyurl.com/7oytud](http://tinyurl.com/7oytud) **Known issues**

*   in order to take full advantage of the multi-arch feature, you'll need:
    *   updated client packages
    *   recreate the stored profiles
*   bad news is that Spacewalk running on Fedora is not yet available. The good news is that we have started building packages to work with Fedora 10. :)
*   [480233](https://bugzilla.redhat.com/show_bug.cgi?id=480233) - deleting stored profiles causes ISE
*   [479640](https://bugzilla.redhat.com/show_bug.cgi?id=479640) - do not conflict with specspo. Work around is to rpm -e specspo.

**Community** A special thanks goes out to Colin Coe for his continued contributions to the apis. Also, thanks to Todd Sanders for his [Telemetry](http://git.fedorahosted.org/git/spacewalk.git/?p=spacewalk.git;a=tree;f=playpen/Telemetry;h=4e91ff77608dda08f262834d0ada9250fb385161;hb=HEAD) contribution. See contributors from past releases: [https://hosted.fedoraproject.org/spacewalk/wiki/ContributorList](https://hosted.fedoraproject.org/spacewalk/wiki/ContributorList) **Installation Help** [https://hosted.fedoraproject.org/spacewalk/wiki/HowToInstall#Installation](https://hosted.fedoraproject.org/spacewalk/wiki/HowToInstall#Installation)