---
title: 'Candlepin 0.4.11 released'
date: Fri, 26 Aug 2011 17:04:40 +0000
draft: false
tags: [Java, Linux, python, Technology]
categories: [Java, Linux, python, Technology]
type: post
---

Candlepin 0.4.11 has been released. You can get the bits at:

[http://repos.fedorapeople.org/repos/candlepin/candlepin/](http://repos.fedorapeople.org/repos/candlepin/candlepin/)

Make sure you read over the [Setup Guide](https://fedorahosted.org/candlepin/wiki/Setup), which is located at

[https://fedorahosted.org/candlepin/wiki/Setup](https://fedorahosted.org/candlepin/wiki/Setup)

For more information on Candlepin, please visit [our project page](http://candlepinproject.org/).

**Features & Enhancements**

**_client_**

*   group subscriptions based on stacking attribute in the following screens:

*   subscriptions page

*   compliance assistant

*   view available subscription page

*   the cli and gui now denote the state of the subscription: Subscribed, Partially Subscribed, Expired or Not Subscribed.

*   Nag messages now denote the 'Partially Subscribed' state.

*   registration with multiple activation keys now supported

*   `list --available` now shows if a subscription is multi-entitle capable

*   GUI shows an asterisk to denote a subscription is multi-entitle capable

*   config command added to cli enabling editing of the configuration values

*   client tries to optionally heal the system to keep it properly subscribed.

**_server_**

*   the list of consumer's installed product IDs are now stored

*   the candlepin job status stable now stores the consumer uuid for async bind.

*   configuration added to disable batch jobs on a particular node

*   Moved the translations to fedora.zanata.org

**Bugs fixed**

729780

non-existent secure objects throw a 404 instead of a 403.

708058

Server 500 error thrown when user auto-subscribes and has no entitlements

728622

Inconsistent enable config entries

728624

Activation keys are successfully being created with invalid chars

728636

Duplicate activation key error is hard to decipher

729125

Adding pools to an activation key should fail when quantity totalQuantity for a multi-entitlement pool

729070

Adding pools to an activation key should be blocked when specifying a quantity>1 for a non-multi-entitlement pool

728721

NullPointerException thrown when registering with an activation key bound to a pool that requires\_consumer\_type person.

729066

remove logging statement to avoid filling up logs.
---
### Comments:
#### [jmrodri](http://zeusville.wordpress.com/ "jmrodri@gmail.com") - <time datetime="2011-08-26 19:29:22">Aug 5, 2011</time>

Not really. It's still pretty early and honestly not sure how interesting this is for folks.
<hr />
#### [stickStick](http://gravatar.com/stickm13 "stick@miscellaneous.net") - <time datetime="2011-08-26 18:06:40">Aug 5, 2011</time>

So I'm curious outside of the RH/RHN use case have you guys seen any adoption of candlepin for other purposes?
<hr />
