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
---
### Comments:
#### [douglasawh](http://www.unc.edu/~whitdoug "whitdoug@email.unc.edu") - <time datetime="2009-08-12 20:16:08">Aug 3, 2009</time>

I'm curious, why is Oracle not an option for you guys where it's not? It only uses the freeware version of Oracle, no?
<hr />
#### [mairin](http://mihmo.livejournal.com "mairin@linuxgrrl.com") - <time datetime="2009-08-08 02:01:49">Aug 6, 2009</time>

woo woo! congrats :)
<hr />
#### [Juanjo](http://rambleon.usebox.net/ "reidrac@usebox.net") - <time datetime="2009-08-08 04:23:45">Aug 6, 2009</time>

Thank you guys! I'm waiting PostgreSQL support to introduce spacewalk in my company, because I have no chances of success with the Oracle dependency :( Keep on rocking.
<hr />
#### [pvanveen]( "pvanveen84@hotmail.com") - <time datetime="2009-08-08 09:15:48">Aug 6, 2009</time>

Great news. Kudos and many thanks to all the developers! Same as Juanjo I'm looking forward to PostgreSQL support as Oracle is not an option in the environment I work in. Keep up the great work and relentless progress in the PostgreSQL area :-)
<hr />
