---
title: 'Hibernate not suited for normalized databases'
date: Sat, 22 May 2004 22:11:57 +0000
draft: false
tags: [Java]
categories: [Java]
type: post
---

On my current project our database is highly normalized to support high volumes of data. We decided to investigate persistence frameworks with a bias towards [Hibernate](http://www.hibernate.org) which has a reputation for being the best persistence framework at current. While it is well suited for a situation where you have one object per table (seems like a typical paradigm for web applications), it is not suited for heavily normalized tables.

In the past, I've posted about recommending Hibernate (see my [JavaLobby](http://www.javalobby.org) [article](http://www.javalobby.org/thread.jspa?forumID=61&threadID=11370&start=0&mode=flat)), but couldn't find a proper use of it in our application. We have several tables sometimes upto three for a given object. Hibernate doesn't seem to do this. Many have said "Hibernate can handle multiple tables per object" but few have actually explained how to do it. Many have also said, "Why don't you make use one object per table" because we can't change our database tables.

We're going to roll our own mapping and hope for the best. In the process, I will checkout [iBATIS](http://www.ibatis.com) as well as [OBJ](http://db.apache.org/ojb/).

_Other Hibernate entries_

[Angsuman's Blog](http://blog.taragana.com/index.php?p=41)  

If you have examples of an object being loaded from multiple tables and the ability to use hand tuned SQL queries (without the use of [HQL](http://www.hibernate.org/hib_docs/reference/en/html/queryhql.html)) feel free to comment.