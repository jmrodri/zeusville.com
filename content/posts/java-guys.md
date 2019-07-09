---
title: 'Java guys'
date: Tue, 07 Feb 2006 10:53:58 +0000
draft: false
tags: [Java]
categories: [Java]
type: post
---

At work we've gotten a lot more Java guys on different projects. Which is good since I really like Java as a language especially for web applications. But since I've been here I've learned to use the best tools for the job and only introduce large Java frameworks when they are needed to solve a problem.

A friend of mine once told me that [Hibernate](http://www.hibernate.org) and

[Struts](http://struts.apache.org) were "crutches". I disagreed with him. But I knew these tools solve a problem and solve it well. But I finally understand what he means.

We Java guys always reach for our frameworks without really thinking if they are too much

for the problem at hand.

For instance, when we embarked on our project, we started to write our own persistence

layer. Daunting yes. Though we figured we can use JDBC until our application out grows

it. After a few weeks of coding, we realized we were recreating Hibernate. So we

dumped it and introduced Hibernate. Some might say "see if you would've chosen Hibernate

to begin with you wouldn't have wasted a few weeks". I disagree because we wanted to see

if it was needed or not.

Struts was a bit different. We went with it for several reasons. Servlet programming

sucks, and many members of the team didn't know Struts which required a good amount of

reading material to be available. WebWork was a good alternative but at the time

books and other training material was non-existent. JSF I'm not quite sold on yet.

Now I've digressed, what I was trying to get at was that this new group of

Java guys reached for all of their favorite tools even though some of the problems

could be solved in a simpler way. The flurry of J2EE jargon is flying everywhere:

Spring, Hibernate, SOAP, SOA, ESB (Enterprise Service Bus), and Mule. Sometimes

I wonder if we Java guys have lost our ability to write software without bringing

in a truck load of heavyweight tools.