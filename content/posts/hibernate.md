---
title: 'Hibernate'
date: Wed, 04 Feb 2004 14:14:23 +0000
draft: false
tags: [Java]
type: post
---

I've been thinking of converting our object model to using [Hibernate](http://www.hibernate.org/) instead of our proprietary persistence framework. Though I like our current implementation, it is difficult to understand and the mapping between domain object and database is done in code instead of a configuration file.

I'm having a difficult time determining if Hibernate can handle a single domain object being stored in three tables. I'll do some experiments on this.