---
title: 'can I have a do over?'
date: Thu, 24 Dec 2009 14:18:04 +0000
draft: false
tags: [Java, Linux, python, Technology]
categories: [Java, Linux, python, Technology]
type: post
---

The next webapp I write, I think I'm going with some of the new hotness: [NoSQL](http://en.wikipedia.org/wiki/NoSQL) datastore, [REST](http://en.wikipedia.org/wiki/Representational_State_Transfer)ful API, and Ruby. On a recent project I chose to use a RESTful API which I really like, but it definitely changes how you think of things coming from the [XML-RPC](http://www.xmlrpc.com) way of doing APIs, but I still like its simplicity.

Unfortunately, I went with Java as the implementation instead of something like [python](http://www.python.org/) or [Ruby](http://www.ruby-lang.org/en/), and looking back I don't know why I did that. I should know by now that [python](http://www.python.org) and [Ruby](http://www.ruby-lang.org/en/) are much easier to work with than Java has proven to. Hell even the build environment is a pain: [ant](http://ant.apache.org/) - write xml build file from scratch, [maven](http://maven.apache.org/) - reminds me of [make](http://www.gnu.org/software/make/) with lot's of pom.xml files, or [buildr](http://buildr.apache.org/) - ruby based maven replacement, annoys all Java people. If I had a do over on this I'd choose Ruby as the implementation language.

Since we're using Java and needed a database we went with [Hibernate](http://www.hibernate.org). If I had to redo this decision, I most certainly would've gone with a NoSQL datastore like [MongoDB](http://www.mongodb.org/display/DOCS/Home) or [CouchDB](http://couchdb.apache.org/), this way I could avoid the annoying mapping of domain model to relational tables which is highly annoying.

So if you're planning a new webapp avoid the boring, traditional webapp design of using a relational database with ORM and [compiled languages](http://java.com/en/) :)