---
title: 'Mysterious Connection Closing (part deux)'
date: Fri, 19 Aug 2005 23:30:15 +0000
draft: false
tags: [Java]
categories: [Java]
type: post
---

If you recall, on [2005-08-17](http://jroller.com/page/jmrodri/20050817) I was having a little problem with a JDBC connection being closed. After a few days of investigation, we have not found the actual culprit, but have found the condition under which said problem occurs.

If the application remains idle for more than two (2) hours, netstat has revealed there are no connections to port 1521, hence no JDBC connections. Hitting said application with requests after the two hour idle causes wonderful "Closed Connection" exceptions. We still can't find "what" is closing these connections

but we suspect it has something to do with our staging environment as this problem does not occur in QA, development demo server, nor on any of the developers workstations.

The other part of the puzzle, the 500 errors which occur because of the closed

connections, is partly because we were using Hibernate's internal connection pooling which is totally worthless except for initial development. Turns out it's an FAQ [When I leave Hibernate running overnight, I come back and find that it can no longer connect to the database](http://www.hibernate.org/117.html#A13). After reading that I was like, DOH! That sounds like our problem.

We didn't want to simply turn on c3p0 without knowing what was closing our

connections. While we investigated, we delved into the Hibernate default

connection pooling code. At the very beginning it prints out "... (not for production use)". ARGH! Can't believe that's actually at **info** level instead of **WARNING**. The code doesn't

check to see if the connections in the pool are valid or idle. If a connection is closed, and returned to the pool, it will be handed out to the unsuspecting code. The pool uses a crappy FILO algorithm which leads bad connections constantly being used. That was enough to convince us to switch.

So we configured [Hibernate to use](http://www.hibernate.org) [c3p0](http://sourceforge.net/projects/c3p0). C3p0 is definitely a more robust connection pool implementation with the ability to check the connections if they are idle for a certain amount of time, etc. For more information on configuring Hibernate with c3p0, check out this [link](http://www.hibernate.org/214.html).

Unfortunately, this was a gross oversight of our team which luckily manifested itself prior to going live. We'll now be more vigilant of these types of problems in the future.