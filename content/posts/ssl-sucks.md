---
title: 'SSL sucks'
date: Fri, 13 Jun 2014 04:02:04 +0000
draft: false
tags: [Java, Technology]
categories: [Java, Technology]
type: post
---

I swear every time I start going down the SSL path I get similar errors and never remember what they mean. Trying to get my app talking to qpid broker using the JMS client.

`Caused by: javax.net.ssl.SSLException: Received fatal alert: bad_certificate`

`at sun.security.ssl.Alerts.getSSLException(Alerts.java:208) ~[na:1.7.0_55]`

`at sun.security.ssl.SSLEngineImpl.fatal(SSLEngineImpl.java:1630) ~[na:1.7.0_55]`

`at sun.security.ssl.SSLEngineImpl.fatal(SSLEngineImpl.java:1598) ~[na:1.7.0_55]`

`at sun.security.ssl.SSLEngineImpl.recvAlert(SSLEngineImpl.java:1767) ~[na:1.7.0_55]`

`at sun.security.ssl.SSLEngineImpl.readRecord(SSLEngineImpl.java:1063) ~[na:1.7.0_55]`

`at sun.security.ssl.SSLEngineImpl.readNetRecord(SSLEngineImpl.java:887) ~[na:1.7.0_55]`

`at sun.security.ssl.SSLEngineImpl.unwrap(SSLEngineImpl.java:761) ~[na:1.7.0_55]`

`at javax.net.ssl.SSLEngine.unwrap(SSLEngine.java:624) ~[na:1.7.0_55]`

`at org.apache.qpid.transport.network.security.ssl.SSLReceiver.received(SSLReceiver.java:102) ~[qpid-common-0.22.jar:na]`

`... 3 common frames omitted`
---
### Comments:
#### 
[thyrsus1]( "sschaefer@acm.org") - <time datetime="2014-06-13 03:57:59">Jun 5, 2014</time>

Tell me about it. The last two days - 16 hours spent - I was trying to authenticate a web page against SSL encapsulated LDAP. If you don't SSL encapsulate it, the password goes across the net in the clear, which I find unacceptable. It turns out that any failure in the mod\_authnz\_ldap and/or mod\_ldap modules kill the Apache thread with no error messages, just 500 - internal server error. Strike 1. The module appears incapable of following a signing chain, and seems to require every certificate in the chain, from the ultimate CA to the the subauthority to the LDAP server (I'm lucky my chain is only three long) listed in the LDAPTrusedGlobalCert - it doesn't seem to know how to chain the signatures. Strike 2. Then, if I get the crazy notion that I should avoid Man-In-The-Middle attacks by actually verifying the signatures with "LDAPVerifyServerCert on" - httpd crashes without error messages again (aside from 500 - internal server error). That last acutally doesn't crash in RHEL/CentOS5 but does in RHEL/CentOS 6. I'm "lucky" enough to be able have a CentOS5 system I can use for this. All of those problems have bugs filed against them, but they're all closed with "can't replicate" type status message, despite there being dozens of frustrated questions on ServerFault.com and similar sites as soon as you start to Google for solutions. I hope the recent "resources" being expended on openssl will not only fix that core but also cleanse the whole environment.
<hr />
#### 
[thyrsus1]( "sschaefer@acm.org") - <time datetime="2014-06-13 15:00:23">Jun 5, 2014</time>

I did get it working under CentOS 5, I just needed to rant that it was a lot harder than it should have been. Thanks for the nginx tip; I'll remember that when I need to update.
<hr />
#### 
[Pieter]( "pvanveen84@hotmail.com") - <time datetime="2014-06-13 04:30:48">Jun 5, 2014</time>

Unhelpful error messages like this really suck. Are you sure your client, server, (intermediate-)CA certificates are ok with the entire certificate chain available/accesible (I guess on both sides)? Can the client and server certificate be succesfully verified by the other side? Certificates are tough. I hope you figure out how to make it work. @thyrsus1 I had the same experience with Apache on CentOS 6.5 x86\_64. There was no way I could make it work either. Frustrating indeed. I switched to nginx and nginx\_auth\_ldap git rev ee45bc4 from https://github.com/kvspb/nginx-auth-ldap (later git revs of work in progress didn't work for me) and this has been working fine for quite some time. Just make sure an ldaprc file with proper ownership & rights is available in the root directory of your webapp (e.g. /usr/share/nginx//).
<hr />
