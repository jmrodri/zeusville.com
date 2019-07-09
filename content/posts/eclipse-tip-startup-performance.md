---
title: 'Eclipse Tip: Startup Performance'
date: Wed, 26 May 2004 16:16:03 +0000
draft: false
tags: [Java]
categories: [Java]
type: post
---

I was a bit concerned with [Eclipse's](http://www.eclipse.org) startup performance. It was taking 12 seconds to start up on a machine with dual XEON's a gig of RAM running [Red Hat](http://www.redhat.com) Enterprise Linux ([RHEL](http://www.redhat.com/software/rhel/)). I started digging. I came across a blog which had the following parameters:

\-vmargs -Xverify:none -XX:+UseParallelGC -XX:PermSize=20M
\-XX:MaxNewSize=32M -XX:NewSize=32M -Xmx160m -Xms160m

Using these parameters my startup went down to 6 seconds!

Sources:
[The Blue Pill](http://weblogs.flamefew.net/moatas/archives/000792.html)
[Running Eclipse](http://download2.eclipse.org/downloads/documentation/2.0/html/plugins/org.eclipse.platform.doc.user/tasks/running_eclipse.htm)
---
### Comments:
#### [Will Gayther]( "jroller.com@jweblog.com") - <time datetime="2004-05-26 18:51:18">May 3, 2004</time>

I tested something like this a while back, and found that only -Xverify:none made any actual difference in startup time - although that one parameter is pretty effective.
<hr />
#### [pope]( "alexandru.popescu@evolva.ro") - <time datetime="2004-05-27 06:47:59">May 4, 2004</time>

This series of parameters were used a lot for starting up Netbeans quickier (on the times when it starts after you finished your work in Eclipse :-) ).
<hr />
#### [Jwahar Raju Bammi]( "bammi@memento-inc.com") - <time datetime="2004-11-10 18:04:21">Nov 3, 2004</time>

i found adding -server improves performance too (not necessarily startup)
<hr />
#### [Tratamiento de Agua](http://www.aquapurificacion.com/albercas.htm "ogramire@aol.com") - <time datetime="2004-11-28 23:32:25">Nov 0, 2004</time>

saludos [http://www.aquapurificacion.com](http://www.aquapurificacion.com)
<hr />
#### [Osmosis Inversa](http://www.ciberteca.net "alan@aol.com") - <time datetime="2006-05-31 00:56:19">May 3, 2006</time>

Como estan todos
<hr />
