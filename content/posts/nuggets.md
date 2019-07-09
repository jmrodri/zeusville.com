---
title: 'Nuggets'
date: Thu, 29 Oct 2009 02:13:22 +0000
draft: false
tags: [Java, Technology]
categories: [Java, Technology]
type: post
---

Here are some of the great nuggets from the [link](http://zeusville.wordpress.com/2009/10/28/link-sharing/) I posted tonight.

So GWT tries to hide Javascript from Java programmers, the same way Hibernate and other ORMs try to hide the database. How many of you use ORMs? How many of you have run into this problem? On Spacewalk we ran into this a lot, so much so we gave up on Hibernate for any other than loading an object for editing, in favor of straight [SQL stored in an XML](http://bit.ly/3a0jmw) file.

> "This is the same basic problem with ORMs like Hibernate: Object-relational impedance mismatch. Every now and again you end up spending half a day figuring the correct combination of properties, annotations, XML and VM parameters to have a query generate the right two lines of SQL that’ll actually be performant."

Another thing I've always said to my management and team members was exactly this. That's why I'm against open coding environments.

> "We all know that knowledge workers work best by getting into "flow", also known as being "in the zone", where they are fully concentrated on their work and fully tuned out of their environment. They lose track of time and produce great stuff through absolute concentration. This is when they get all of their productive work done. Writers, programmers, scientists, and even basketball players will tell you about being in the zone.
> 
> The trouble is, getting into "the zone" is not easy. When you try to measure it, it looks like it takes an average of 15 minutes to start working at maximum productivity.
> 
> The other trouble is that it's so easy to get knocked out of the zone. Noise, phone calls, going out for lunch, having to drive 5 minutes to Starbucks for coffee, and interruptions by coworkers -- especially interruptions by coworkers -- all knock you out of the zone.
> 
> "

And as I stated in my [Overengineered Project](http://zeusville.wordpress.com/2009/10/23/old-overengineered-project/) post., Java devs like to over engineer solutions in favor of flexibility that may or may not happen.

> "What’s more Java programmers have a predilection with concerning themselves about swapping out layers or putting in alternative implementations that never happen.
> 
> I am a firm believer that lines of code are the enemy. "

And we're totally guilty of these layers as well, even on project Spacewalk we can see some of these things in practice. We

have a [Manager](http://bit.ly/dR6WI) layer, a [UI](http://bit.ly/1m51Ya) layer, not to mention a [database](http://bit.ly/2C5UKq) layer :)

> "It’s not \[sic\] secret that Java programmers love their layers. No sooner do you have a Presentation Layer, a Controller Layer and a Repository Layer than someone suggest you also need a Database Abstraction Layer, a Service Layer, a Web Services Layer and a Messaging Layer."

So what can you learn from all this? [KISS](http://en.wikipedia.org/wiki/KISS_principle)!