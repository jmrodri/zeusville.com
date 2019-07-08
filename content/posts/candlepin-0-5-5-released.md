---
title: 'Candlepin 0.5.5 released'
date: Thu, 08 Dec 2011 20:17:38 +0000
draft: false
tags: [candlepin, Java, java, Linux, python, python, Technology, thumbslug]
type: post
---

![Candlepin](http://candlepinproject.org/images/logo-frontpage.png "Candlepin") It's that time again, another release of Candlepin and associated projects available for your enjoyment. With this release we have [subscription-manager](https://fedorahosted.org/subscription-manager/) in Fedora as well as a debut build of [Thumbslug](https://fedorahosted.org/candlepin/wiki/thumbslug/Index). For more information on Candlepin, please visit: [http://candlepinproject.org/](http://candlepinproject.org/) **Features & Enhancements** **_subscription-manager_**

*   added support for host registration and guest association when host can not register itself
*   virt-who work to handle ESX guests
*   subscription-manager available in fedora

**_candlepin_**

*   build modified to use the tito hotness instead of bunch of disjoint bash scripts
*   disable manifest rules import
*   added support for host registration and guest association when host can not register itself

**_thumbslug_**

*   added appropriate init scripts to run as a service
*   uses Candlepin CRL
*   thumbslug talks to akamai
*   created puppet module for katello

**Bugs fixed** **_subscription-manager_**

[705883](https://bugzilla.redhat.com/show_bug.cgi?id=705883)

Fix error dialog modal issues.

[719743](https://bugzilla.redhat.com/show_bug.cgi?id=719743)

Improved text output for successful pool subscription

[740788](https://bugzilla.redhat.com/show_bug.cgi?id=740788)

Getting error with quantity subscribe using subscription-assistance page.

[746259](https://bugzilla.redhat.com/show_bug.cgi?id=746259)

Don't allow the user to pass in an empty string as an activation key

[746732](https://bugzilla.redhat.com/show_bug.cgi?id=746732)

Only use fallback locales for dates we need to parse

[749332](https://bugzilla.redhat.com/show_bug.cgi?id=749332)

Normalize the error messages for not being registered

[749636](https://bugzilla.redhat.com/show_bug.cgi?id=749636)

Client should not support users entering activation keys and existing consumer ids

[752572](https://bugzilla.redhat.com/show_bug.cgi?id=752572)

add interval logging statements back in on rhsmcertd startup

[753093](https://bugzilla.redhat.com/show_bug.cgi?id=753093)

The available subscriptions count does not show correctly in Subscription Manager GUI

[754821](https://bugzilla.redhat.com/show_bug.cgi?id=754821)

Default org of "Unknown" was not marked for gettext

[755031](https://bugzilla.redhat.com/show_bug.cgi?id=755031)

Unregister before attempting to run a second registration

[755035](https://bugzilla.redhat.com/show_bug.cgi?id=755035)

Migration script should work on RHEL 5.7 and up.

[755130](https://bugzilla.redhat.com/show_bug.cgi?id=755130)

add extra whitespace to classic warning

[755541](https://bugzilla.redhat.com/show_bug.cgi?id=755541)

Enhanced the message in the katello plugin to debug when the backend system does not support environments.

[756173](https://bugzilla.redhat.com/show_bug.cgi?id=756173)

Unexpected behavior change in subscription-manager unregister

[756507](https://bugzilla.redhat.com/show_bug.cgi?id=756507)

do not use output from "getlocale" as input for "setlocale"

[758471](https://bugzilla.redhat.com/show_bug.cgi?id=758471)

install-num-migrate-to-rhsm threw traceback when no instnum was found.

[759199](https://bugzilla.redhat.com/show_bug.cgi?id=759199)

rhsmcertd is logging the wrong value for certFrequency

**_candlepin_**

[753093](https://bugzilla.redhat.com/show_bug.cgi?id=753093)

The Available Subscriptions count do not show correctly in Subscription Manager GUI

[754841](https://bugzilla.redhat.com/show_bug.cgi?id=754841)

Implement DELETE /pools/id.

[754843](https://bugzilla.redhat.com/show_bug.cgi?id=754843)

Fix legacy virt bonus pools missing pool\_derived.

[755677](https://bugzilla.redhat.com/show_bug.cgi?id=755677)

Activation Keys should not check quantity on unlimited pools

[756628](https://bugzilla.redhat.com/show_bug.cgi?id=756628)

Translate missing rule errors.

[758462](https://bugzilla.redhat.com/show_bug.cgi?id=758462)

ensure job detail isn't null, skip it.

**_thumbslug_**

[759607](https://bugzilla.redhat.com/show_bug.cgi?id=759607)

update url for subscriptions handler

**Download & Setup** Make sure you read over the [Candlepin Setup Guide](https://fedorahosted.org/candlepin/wiki/Setup), which is located at [https://fedorahosted.org/candlepin/wiki/Setup](https://fedorahosted.org/candlepin/wiki/Setup). As well as the [Headpin Install Guide](https://fedorahosted.org/candlepin/wiki/headpin/Install) which can be found at [https://fedorahosted.org/candlepin/wiki/headpin/Install](https://fedorahosted.org/candlepin/wiki/headpin/Install) Just give me the bits already! You can get the various bits at the urls below. Candlepin: [http://repos.fedorapeople.org/repos/candlepin/candlepin/](http://repos.fedorapeople.org/repos/candlepin/candlepin/) Thumbslug: [http://repos.fedorapeople.org/repos/candlepin/thumbslug/](http://repos.fedorapeople.org/repos/candlepin/thumbslug/) Headpin: [http://repos.fedorapeople.org/repos/katello](http://repos.fedorapeople.org/repos/katello) Subscription Manager: [http://repos.fedorapeople.org/repos/candlepin/subscription-manager/](http://repos.fedorapeople.org/repos/candlepin/subscription-manager/)