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
---
### Comments:
#### 
[Jeff]( "jweiss@redhat.com") - <time datetime="2009-12-24 18:49:34">Dec 4, 2009</time>

I am trying to write a single app that can handle defect tracking, testcase tracking, personal tasks, agilo type stuff,etc. Since those apps are all pretty much do the same thing (save records with multiple fields and a workflow, let you search them and give reports), why not have it all integrated, right? I want each domain to just be data in the database, and the application just handles the generic logic. Turns out the main thing standing in my way was relational db's, they're not flexible enough. So I started playing around with couchdb, which as it turns out, is almost all you need to write the entire app. Not quite though, and even if I could, my javascript-fu is weak. So I decided to use my favorite language du jour, clojure, to do the rest. It has a restful, lispy, rails-like library called compojure. Hopefully it'll turn out well.
<hr />
#### 
[John W]( "wregglej@gmail.com") - <time datetime="2009-12-24 12:04:47">Dec 4, 2009</time>

Cassandra and Tokyo Tyrant are a couple more nifty NoSQL datastores. Personally, I'd choose Cassandra over TT, even if Cassandra is implemented in Java. http://incubator.apache.org/cassandra/ http://1978th.net/tokyotyrant/
<hr />
