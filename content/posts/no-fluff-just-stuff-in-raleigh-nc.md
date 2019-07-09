---
title: 'No Fluff Just Stuff in Raleigh, NC'
date: Mon, 14 Jun 2004 12:18:13 +0000
draft: false
tags: [Java]
categories: [Java]
type: post
---

This weekend I attended [No Fluff Just Stuff](http://www.nofluffjuststuff.com/index.jsp) this weekend. It was an excellent conference. It was small and personal, with great speakers, awesome topics, and no sales pitches.

I'll start with the complaints first. The temperature in the rooms at the hotel were extremely cold, every day we had to have the temperature adjusted. They were not setup to take credit cards for purchases, if they did I probably would've bought some books. I guess that's actually a good thing since it saved me money. Those were the only complaints I really had.

The conference was great, much different than JavaONE, which I attended in 1999. The only good talks I liked at JavaONE were the ones by authors and consultants who had real world examples and problems. The [Sun](http://www.sun.com) hosted sessions felt like sales pitches. I can't comment on how it will be this year.

The symposium was three days June 11 - 13. On Friday, I attended "Decoupling Patterns" by Dave Thomas, "Rapid User Interface Development with Tiles" by David Geary, and "Introduction to Spring" by Bruce Tate.

Dave Thomas did an excellent job pointing out ways to decouple your code to make it easier to test and change in the future. He mentioned that many of us, including me, put classes in packages but we allow all other packages access to the classes. This causes coupling from one package to another. He suggested adding a facade to the package, while all other classes are package private. A lightbulb went on in my head. This is a great idea. Effectively, this gives you encapsulation at the package level as well as the class level.

Since we're looking at using Tiles for our layout, I figured "Rapid User Interface Development with Tiles" would be a great talk. Unfortunately, I found the talk too basic. And David Geary didn't do enough demos. I think 15 - 20 minutes intro to what Tiles is and isn't, then jump into a demo would've made a better presentation.

After a bit of disappointment with the [Tiles](http://jakarta.apache.org/struts/userGuide/dev_tiles.html) demo, I attended Bruce Tate's "Introduction to Spring". The [Spring Framework](http://www.springframework.org/) is a lightweight container that uses "Inversion of Control" or as Martin Fowler calls it ["Dependency Injection"](http://www.martinfowler.com/articles/injection.html). From what I could see Spring looks like an excellent way to "decouple" your entire web application. By using an XML configuration file you can connect the different pieces in your application. Spring uses setter injection to connect the pieces together. It is a refreshing alternative to the heavy weight containers used for typical J2EE applications.

The first day of the conference was great. On Saturday, I had the following sessions to attend: "Pragmatic Mock Objects" by Dave Thomas, "eXtreme Struts" by David Geary, "Better, faster, lighter Java" by Bruce Tate, and finally "Test driven development" by Mike Clark.

Once again, Dave Thomas, delivered an excellent talk explaining when to use Mock Objects for testing and development. And by using Mock Objects you end up refactoring your code making it less "coupled".

I was looking forward to "eXtreme Struts". I wanted to know what you could do with this framework that some say is great and others hate. But I was completely disappointed with this presentation. It was a repeat of the Tiles presentation. In David's defense, this was the first time he gave this talk so his timing was off. But still, I expected more extreme from this talk.

At lunch I had a good discussion with my co-workers, Chip and Robin, and two presenters, Dave Thomas and Mike Clark. We all agreed that Hibernate, Spring are not the silver bullet. And that simply choosing a framework because it seems everyone else is using it was a bad idea. Even Bruce Tate stated, if JDBC and POJO's work for you, then continue to use them until they no longer solve you're problem.

After lunch, I attended Bruce Tate's "Better, faster, lighter Java" presentation did a good job giving you an overview of developing a J2EE application with lighter frameworks. This talk was an extension of the "Intro to Spring" and went into more "good advice".

I ended the day with Mike Clark's "Test Driven Development". This was an awesome presentation and gave me the testing bug. I think that unit tests make better documentation than Javadoc. Mike pointed out that Javadoc becomes stale and misleading. Where as unit tests are always up to date, otherwise, they either won't compile or won't pass. I'm going to propose we add more unit tests to our development process and less useless Javadoc (like for getters and setters).

WHEW! That was Saturday. By this point, I'm excited about all of the new stuff I've learned, and mentally exhausted.

Sunday rolls around and trek back out to RTP from Wake Forest. And stupid me whizzes past the Miami Blvd exit. ARGH! So I turn around and was 5 minutes late to Erik Hatcher's "Tapestry by Example" presentation. Erik did a superb job in this presentation. He built a web application using Tapestry from the ground up. And he was well organized with an Ant script that could skip forward in steps in case the examples weren't going well.

[Tapestry](http://jakarta.apache.org/tapestry/) looks like a great web framework allowing you to deal with real objects on a page instead of name/value pairs from a Request. But I'm not too keen on the markup language used by Tapestry, it uses regular HTML tags with a jwcid attribute which indicates to Tapestry that this is a Java Web Component. The primary reason for this is to allow web designers design web pages while developers get to the nitty gritty. But I haven't worked on a project where the web designers weren't developers as well. So this feature isn't as compelling for me as it may be to others. The other thing that bothered me about it was the lack of a Tiles like templating or the ability to create a layout to be used by the entire site. I will play with Tapestry in my spare time, the little that I have, to see how usable it is.

After the 3 hour session on Tapestry, we had lunch. Then back to another Erik Hatcher talk on "Lucene in Action". Erik's knowledge of [Lucene](http://jakarta.apache.org/lucene/docs/index.html) was evident in his ability to answer all of my questions without even flinching. My concerns over Lucene's internationalization capabilities were answered. Lucene looks like a great way to add searching to your web application. Erik also noted that Lucene has other language bindings like PLucene for Perl, PyLucene for Python, CLucene for C, and Lucene.NET for .NET.

After the Lucene talk, I needed to decide what my final session of the symposium would be. I chose "Metaprogramming" by Stuart Halloway. Stuart is a great speaker. And in his talk he created some heated discussions with some of his presentation. He also provoked thought. If you get a chance to see Stuart speak I strongly recommend it.

That was my view of the No Fluff Just Stuff conference here in Raleigh-Durham.