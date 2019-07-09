---
title: 'can I have a do over?'
date: Thu, 24 Dec 2009 14:18:04 +0000
draft: false
tags: [Java, Linux, python, Technology]
categories: [Java, Linux, python, Technology]
type: post
---


#### 
[Jeff]( "jweiss@redhat.com") - <time datetime="2009-12-24 18:49:34">Dec 4, 2009</time>

I am trying to write a single app that can handle defect tracking, testcase tracking, personal tasks, agilo type stuff,etc. Since those apps are all pretty much do the same thing (save records with multiple fields and a workflow, let you search them and give reports), why not have it all integrated, right? I want each domain to just be data in the database, and the application just handles the generic logic. Turns out the main thing standing in my way was relational db's, they're not flexible enough. So I started playing around with couchdb, which as it turns out, is almost all you need to write the entire app. Not quite though, and even if I could, my javascript-fu is weak. So I decided to use my favorite language du jour, clojure, to do the rest. It has a restful, lispy, rails-like library called compojure. Hopefully it'll turn out well.
<hr />
#### 
[John W]( "wregglej@gmail.com") - <time datetime="2009-12-24 12:04:47">Dec 4, 2009</time>

Cassandra and Tokyo Tyrant are a couple more nifty NoSQL datastores. Personally, I'd choose Cassandra over TT, even if Cassandra is implemented in Java. http://incubator.apache.org/cassandra/ http://1978th.net/tokyotyrant/
<hr />
