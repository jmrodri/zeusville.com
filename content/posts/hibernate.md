---
title: 'Hibernate'
date: Wed, 04 Feb 2004 14:14:23 +0000
draft: false
tags: [Java]
categories: [Java]
type: post
---

I've been thinking of converting our object model to using [Hibernate](http://www.hibernate.org/) instead of our proprietary persistence framework. Though I like our current implementation, it is difficult to understand and the mapping between domain object and database is done in code instead of a configuration file.

I'm having a difficult time determining if Hibernate can handle a single domain object being stored in three tables. I'll do some experiments on this.
---
### Comments:
####
[Juha Komulainen](http://www.jroller.com/page/komu "komu@iki.fi") - <time datetime="2004-02-04 14:30:04">Feb 3, 2004</time>

I think that currently it is not possible, but according to http://hibernate.org/Documentation/RoadMap it seems that it's coming in 2.2. The stance of Hibernate developers seems to be that your domain model should be at least as granular as your database schema. (And I think it's a good advide, although probably not very helpful in your current situation.)
<hr />
####
[Sam Newman](http://www.magpiebrain.com/ "sam-newman@magpiebrain.com") - <time datetime="2004-02-06 10:16:10">Feb 5, 2004</time>

My (limited) experience seems to back that up - one table = one object. That said, use a Data Mapper/DAO and hide the persistence method, then have your Hibernate implementation merge an object together. Hibernate does have good support for object relationships which might do what you want (for example you load a team and Hibernate can lazy load all the player objects for you too). Personally I've never used the object-across-three-tables approach primarily due to the performance issues concerning joins.
<hr />
