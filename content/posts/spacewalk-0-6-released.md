---
title: 'Spacewalk 0.6 RELEASED'
date: Sat, 08 Aug 2009 01:49:01 +0000
draft: false
tags: [Linux, spacewalk]
categories: [Linux, spacewalk]
type: post
---

[![](http://www.redhat.com/spacewalk/img/spacewalk-logo.png "Spacewalk")](https://hosted.fedoraproject.org/spacewalk/)

Spacewalk 0.6 is finally here! In a few hours, Spacewalk 0.6 will be available for installing. With this release, as with previous releases, Spacewalk 0.4 will no longer be available for download.

`http://spacewalk.redhat.com/yum/0.6/RHEL/5/os/`

`http://spacewalk.redhat.com/yum/0.6/Fedora/10//os/`

`http://spacewalk.redhat.com/yum/0.6/Fedora/11//os/`

Make sure to read over the [Installation Guide](http://fedorahosted.org/spacewalk/wiki/HowToInstall#Installation) again. If you are upgrading from 0.5 to 0.6, please checkout:

[http://fedorahosted.org/spacewalk/wiki/HowToUpgrade](http://fedorahosted.org/spacewalk/wiki/HowToUpgrade)

**Features & Enhancements**

*   Spacewalk 0.6 is available for Fedora 11!

*   support for [SHA256](https://fedorahosted.org/spacewalk/wiki/Sha256Support) in rpm

*   large (2+GB) rpm support (requires rpm 4.6)

*   ability to [import a yum repo](https://hosted.fedoraproject.org/spacewalk/wiki/YumImport) into a channel
    
    [https://fedorahosted.org/spacewalk/wiki/UploadFedoraContent](https://fedorahosted.org/spacewalk/wiki/UploadFedoraContent)
    

*   script based reporting: [http://bit.ly/NyCrj](http://bit.ly/NyCrj)

*   fix jabberd that was broken in Spacewalk 0.5

*   KVM support

*   and more [APIs](https://hosted.fedoraproject.org/spacewalk/wiki/ApiAdditions):
    
    *   errata.delete
    
    *   channel.software.uploadPackage
    
    *   monitoring.\*
    
    *   org.list\*Entitlements
    
    *   packages.getDetails
    
    *   system.config.scheduleImport
    

**Bugs fixed**

This release fixed approximately 120 bugs - [http://bit.ly/14ahTW](http://bit.ly/14ahTW)

**Known issues**

*   PostgreSQL support does not work, but the infrastructure has  been committed. We will need help with moving this forward.

*   Fedora GPG key not recognized by rhnPackageKey table, packages will show up as unknown Provider.

*   Documentation search does not work, other search are unaffected.

**Community**

We greatly appreciate the contributions the community has made to  this release. Thank you very much.

*   Gurjeet Singh

*   Joshua Roys

*   Mark Chappell

*   Maxim Burgerhout

*   Muhammad Farrukh

*   Satoru SATOH

*   Tom Lane

*   Vikram Rai

Do you want to get your name on the _**AWESOME**_ [Contributors List](http://fedorahosted.org/spacewalk/wiki/ContributorList)? Simply [submit a patch](https://hosted.fedoraproject.org/spacewalk/wiki/GitGuide#SubmittingPatches).

**Installation Help**

[http://fedorahosted.org/spacewalk/wiki/HowToInstall#Installation](http://fedorahosted.org/spacewalk/wiki/HowToInstall#Installation)