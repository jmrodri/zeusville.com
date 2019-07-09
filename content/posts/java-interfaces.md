---
title: 'Java Interfaces'
date: Wed, 01 Oct 2003 15:17:20 +0000
draft: false
tags: [Java]
categories: [Java]
type: post
---

One of my pet peeves is when an interface is created and implemented yet the code expecting the interface simply casts it to a concrete class. My philosophy is that if my class implements an interface and I pass it into a method which expects an object that implements an interface, that method should not ASSUME it is getting a particular type of object. ARGH!