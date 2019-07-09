---
title: 'Spacewalk 0.7 RELEASED'
date: Thu, 17 Dec 2009 03:48:04 +0000
draft: false
tags: [Linux, spacewalk]
categories: [Linux, spacewalk]
type: post
---

Sorry for being so late, but I'm happy to see that [Spacewalk 0.7](https://fedorahosted.org/spacewalk/#Spacewalk0.7RELEASED) was released on December 4th, 2009.

Here are some of the features in this release:

*   new script "spacewalk-report" allows you to create reports with output to CSV file [ScriptBasedReporting](https://fedorahosted.org/spacewalk/wiki/Features/ScriptBasedReporting)

*   pages with erratas have column with links to [CVE description](https://fedorahosted.org/spacewalk/wiki/Features/WebuiErrataAndCvesEnhancements), erratas can be filtered by its type

*   Spacewalk can be installed on Fedora 12

*   Top level package spacewalk do not exists any more. It has been split into spacewalk-oracle and spacewalk-postgresql, which depends on oracle or postgresql library. _Note: postgresql version is highly experimental._

*   Spacewalk now tracks date and time of package installation

*   Config channels now can handle symlinks

*   Support for WebUI based KVM guest management & provisioning

*   Spacewalk repositories have been split to server and client parts

*   Base client packages are now in Fedora. That means you are now able to register Fedora machine to Spacewalk, without setting up additional repository

*   [and much more](https://www.redhat.com/archives/spacewalk-announce-list/2009-December/msg00000.html)

Congrats to the Spacewalk team for another great release!
---
### Comments:
####
[Rahul Sundaram]( "sundaram@fedoraproject.org") - <time datetime="2009-12-17 05:18:56">Dec 4, 2009</time>

Can the Postgres version be imported into Rawhide? Would help stabilize it.
<hr />
