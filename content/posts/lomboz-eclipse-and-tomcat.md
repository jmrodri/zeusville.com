---
title: 'Lomboz, Eclipse, and Tomcat...'
date: Fri, 14 Nov 2003 11:33:25 +0000
draft: false
tags: [Java]
type: post
---

I started my J2EE project at home tonight and it's taking a lot longer than I thought. Having worked with proprietary servers for the past three years has caused my J2EE skills to become extremely rusty. Ok who am I kidding, how about non-existent.

![](http://jakarta.apache.org/tomcat/images/tomcat.gif)I installed the [Lomboz v2.1.1](http://www.objectlearn.com) with [Eclipse 3.0](http://www.eclipse.org) and [Tomcat 5.0.14 beta](http://jakarta.apache.org/tomcat/index.html). Lomboz out of the box has support for many servers including [JBoss](http://www.jboss.org), [BEA Weblogic](http://www.bea.com/), and Tomcat. But it doesn't have a [server definition](http://www.objectlearn.com/support/docs/serverDefs.jsp) for Tomcat 5.0 yet. So I attempted to create one. I copied the 4.1.0 entry, renamed it 5.0 and changed the directory locations. After many attempts, I couldn't get the start/stop feature to work from the Lomboz J2EE view. My Tomcat always has the little red exclamation icon.![](http://www.jroller.com/resources/jmrodri/lomboz.png).

I finally gave up and used the build.xml in the Lomboz projects to deploy/undeploy using the [Ant](http://ant.apache.org/) plugin and the [Sysdeo Tomcat plugin](http://www.sysdeo.com/eclipse/tomcatPlugin.html) to start and stop Tomcat.

By the time I finally got this to work, it was 1:00 AM and I desperately needed to go to bed. Hopefully now that I have the setup usable, I can get a bit further with the code. If anyone has a better solution let me know.