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
---
### Comments:
#### [Robin Norwood]( "robin.norwood@gmail.com") - <time datetime="2009-10-28 23:44:13">Oct 3, 2009</time>

\*AHEM\* I'd like to point out that DataSource predates the entire Java stack, including Hibernate, thankyouverymuch. I should know, I wrote it. (Chip had a hand in the design, as I recall - probably most of the good bits are his.) We did it for the reasons you mention, but also to have a central repository and framework for all of the queries we needed to hand-tune for performance reasons. We ended up using it for basically everything that wasn't returning a single object. Everything else you said is right, though. :-)
<hr />
#### [mairin](http://mihmo.livejournal.com "mairin@linuxgrrl.com") - <time datetime="2009-10-29 00:49:42">Oct 4, 2009</time>

Pure potential, complete absence of utility. I'd rather Ray's beat up, ugly, paint-peeled 12-year old Dodge Neon than a beautiful Jaguar that can't move. At least the Neon can get me to the supermarket.
<hr />
#### [rm-rf](http:// "dgoodwin@dangerouslyinc.com") - <time datetime="2009-10-29 08:26:46">Oct 4, 2009</time>

It's dangerous (and too easy) to let dumb trends in Java culture convince us to go too far the opposite direction though. It's worth noting that Spacewalk's Hibernate ORM is about the only piece that isn't binding us to Oracle. Sometimes, you actually need those layers someday. The trick is knowing when you do and when you don't. :)
<hr />
#### [Mickael](https://blog.misc.ephaone.org/ "misc@zarb.org") - <time datetime="2009-10-29 08:51:35">Oct 4, 2009</time>

Just for the record, some ORM exists with a possibility of adding your own queries ( such as http://www.sqlalchemy.org/ in python ).
<hr />
#### [Luke Meyer]( "luke.rt.meyer@gmail.com") - <time datetime="2009-10-29 09:14:38">Oct 4, 2009</time>

careful there, zeus, you're sailing into some dangerously heretical waters for a java programmer! you mean layers of abstraction actually get in the way of optimizing performance? next you'll be saying they make code hard to understand too!
<hr />
#### [chip]( "cturner@pattern.net") - <time datetime="2009-10-29 18:29:03">Oct 4, 2009</time>

zeus!! holy cow. you've come a long way. brings a tear to my eye. oh I remember how lost and scared you were at the heretical rantings oh so many years ago when you realized just what heretics you had joined with. \*sob\*
<hr />
