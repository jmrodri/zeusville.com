---
title: 'Going interface heavy'
date: Thu, 06 Nov 2003 10:53:03 +0000
draft: false
tags: [Java]
categories: [Java]
type: post
---

Recently it was decided that we move towards an interface heavy design to allow more flexibility in our software. I believe interfaces have their place but do not agree that every class in a system should be an implementation of an interface. I find it more useful to use interfaces as the connectors between different parts of a software system to facilitate enhancements, but some portions are just fine being concrete classes or abstract classes.

For instance, if I am passing in a class to a method from one part of a system to another, an interface would be a much better parameter type. This way if I choose to create another implemenation of that interface it will work without changing the recipient method. I recently found this to be of value when I designed a method to take in an interface. When the requirements changed, I simply created a new implementation and passed it into the aforementioned method. It was a great feeling not to have to rework both sides of the code.

But making a system interface heavy doesn't mean to make "everything an interface". To me it means to rely on interfaces to loosely couple different of a system, but still use patterns, abstract, and concrete classes when needed. I'd like to hear others views on this, so feel free to comment.