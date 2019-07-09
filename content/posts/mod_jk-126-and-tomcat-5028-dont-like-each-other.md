---
title: 'mod_jk 1.2.6 and tomcat 5.0.28 don''t like each other'
date: Tue, 18 Jan 2005 18:10:35 +0000
draft: false
tags: [Java]
categories: [Java]
type: post
---

I'm having a hell of a time getting mod\_jk 1.2.6 to work with tomcat 5.0.28. mod\_jk dies a miserable death on every POST to the website.

```
DEBUG TP-Processor8 org.apache.jk.common.ChannelSocket - read() \[B@cf148e5 8192 0 4 = -1
 INFO TP-Processor8 org.apache.jk.common.JkInputStream - Receiving: getting request body chunk -3 4
 INFO TP-Processor8 org.apache.jk.common.JkInputStream - Receiving: getting request body chunk -3 4
 ERROR TP-Processor8 org.apache.jk.common.HandlerRequest - Error decoding request
 java.io.IOException
    at org.apache.jk.common.JkInputStream.receive(JkInputStream.java:252)
    at org.apache.jk.common.HandlerRequest.decodeRequest(HandlerRequest.java:500)
    at org.apache.jk.common.HandlerRequest.invoke(HandlerRequest.java:352)>
    at org.apache.jk.common.ChannelSocket.invoke(ChannelSocket.java:743)>
    at org.apache.jk.common.ChannelSocket.processConnection(ChannelSocket.java:675)
    at org.apache.jk.common.SocketConnection.runIt(ChannelSocket.java:866)
    at org.apache.tomcat.util.threads.ThreadPool$ControlRunnable.run(ThreadPool.java:684)
    at java.lang.Thread.run(Thread.java:567)

```