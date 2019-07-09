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