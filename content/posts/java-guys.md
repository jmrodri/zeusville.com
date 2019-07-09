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
---
### Comments:
#### 
[Jonathan Locke]( "jonl@muppetlabs.com") - <time datetime="2006-02-07 12:21:15">Feb 2, 2006</time>

"JSF I'm not quite sold on yet." http://wicket.sf.net/
<hr />
#### 
[Damien B](http://www.jroller.com/page/kame?catname=%2FJava "kame@cinemasie.com") - <time datetime="2006-02-07 14:11:00">Feb 2, 2006</time>

"JSF I'm not quite sold on yet." http://wicket.sf.net/ "Sometimes I wonder if we Java guys have lost our ability to write software without bringing in a truck load of heavyweight tools." wicket-1.1.1.zip, 6.1MB, more than 500 classes and interfaces in the public API... who said that Java zealots can't read?
<hr />
#### 
[Adrian](http://www.adrianlikins.com "adrian@likins.com") - <time datetime="2006-02-07 14:41:23">Feb 2, 2006</time>

\>Sometimes I wonder if we Java guys have lost our > >ability to write software without bringing in a >truck load of heavyweight tools. Yes, yes you have. ;->
<hr />
#### 
[afsina]( "ahmetaa@gmail.com") - <time datetime="2006-02-07 21:29:54">Feb 2, 2006</time>

just dont use hibernate or struts. you can always use plain jsp and jdbc, or an object oriented database. if your application is simple, it is a pain to use them anyway..
<hr />
#### 
[Phillip Rhodes](http://www.jroller.com/page/mindcrime "mindcrime@cpphacker.co.uk") - <time datetime="2006-02-08 10:27:28">Feb 3, 2006</time>

\[quote\] We Java guys always reach for our frameworks without really thinking if they are too much for the problem at hand.\[/quote\] Speak for yourself. ;-) Seriously, not everybody does that. And there \*are\* times when Java developers reach for Spring or Hibernate or Tapestry or Struts, etc. after careful deliberation, and it's the right choice. I agree with what I think is your point; that the decision to introduce these frameworks is something that needs to be considered carefully and the pros and cons weighed. But they do exist for a reason, they do solve real, legitimate problems, and they often do simplify development. I think it's a bit of a reach to suggest that we, as a whole, have forgotten how to do things without "a truckload of heavyweight tools." And that's without even getting into the whole thing (which Hani hit on a while back in the Bile Blog) of what exactly is a "heavyweight" vs. "lightweight" framework? Is Struts heavyweight? Is Hibernate? If so, how do we know? And are there lightweight alternatives?
<hr />
