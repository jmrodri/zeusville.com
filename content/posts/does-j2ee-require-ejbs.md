---
title: 'Does J2EE require EJBs?'
date: Sun, 04 Apr 2004 21:33:27 +0000
draft: false
tags: [Java]
categories: [Java]
type: post
---

I've stated before that our project needs to move towards J2EE technology. And sometimes I'm "corrected" that I mean J2SE since our project isn't going to use EJBs. Since when does a J2EE application _**require**_ EJBs? Can't a web application be a J2EE application by mearly having JSPs, Servlets, and following the MVC architecture?
---
### Comments:
####
[Matt Raible](http://raibledesigns.com "matt@raibledesigns.com") - <time datetime="2004-04-04 21:39:43">Apr 0, 2004</time>

There's really no reason to use EJBs if you use [Spring](http://www.springframework.org). Maybe if you really need distributed systems - but you could always use web services instead of RMI. To back that up, [this weekend](http://www.springframework.org/news.html#baseBeans), Rod showed us many benchmarks where Spring is faster than EJBs.
<hr />
####
[Marco Campelo](http://www.jroller.com/page/mcampelo "") - <time datetime="2004-04-04 21:47:11">Apr 0, 2004</time>

I'm still looking for a good reason to implements EJBs in my projects. The API is really complex, takes a lot of time to develop and I can achieve the same results using other solutions.
<hr />
####
[Jesus M. Rodriguez](http://www.jroller/page/jmrodri "jmrodri@nc.rr.com") - <time datetime="2004-04-04 22:24:31">Apr 0, 2004</time>

I agree, I see no point using EJBs. But when I say we're developing a J2EE application, would that imply that it uses EJBs? Would you consider Roller a J2EE application?
<hr />
####
[Phillip Calçado](http://www.jroller.com/page/pcalcado "pcalcado@yahoo.com") - <time datetime="2004-04-04 22:33:06">Apr 0, 2004</time>

In fact, there is no reason for not calling this an J2EE project.

[Here](http://java.sun.com/j2ee/overview.html), you can see:
_The Java 2 Platform, Enterprise Edition (J2EE) defines the standard for developing multitier enterprise applications. The J2EE platform simplifies enterprise applications by basing them on standardized, modular components, by providing a complete set of services to those components, and by handling many details of application behavior automatically, without complex programming._

Even a Servlet/JSP can be a J2EE app, what defines being or not is the use of the J2EE APIs and specification. Generally, an J2EE app will work inside a container.

I see this many times...."Let's use J2EE" when people are trying to say the want EJBs. The good thing is that you can use the framework you want and when someone try to complain you just say: "Hey, isn't that J2EE?".

I like EJB's idea, but I believe there's something wrong with the whole thing... by know, what I believe it'd worng is the use of RDBMS for everything...
<hr />
####
[lowem](http://www.jroller.com/page/lowem "spam-me@mailinator.com") - <time datetime="2004-04-05 03:14:40">Apr 1, 2004</time>

The "J2EE=EJB" thing has been at best a misunderstanding, at worst? - deceptive marketing hype. Next time you unzip Tomcat from distribution and run its welcome page, you can tell yourself, "hey, this is a J2EE app" and dare anyone else to challenge you on it ... :)
<hr />
####
[Jesus M. Rodriguez](http://www.jroller.com/page/jmrodri "jmrodri@nc.rr.com") - <time datetime="2004-04-05 11:40:52">Apr 1, 2004</time>

Thanks folks. That's what I thought. A web application with Servlets & JSPs is still a J2EE application.
<hr />
####
[Jason Carreira](http://jroller.net/page/jcarreira "jason@zenfrog.com") - <time datetime="2004-04-05 12:30:39">Apr 1, 2004</time>

Unfortunately, there is something to the statement that it's not J2EE without EJB. An application from an ISV can't be certified as a J2EE application if it only uses Servlets and not EJB. Just ask the guys at Atlassian.
<hr />
####
[Dan Hinojosa](http://www.evolutionnext.com "dhinojosa@evolutionnext.com") - <time datetime="2004-04-05 13:12:28">Apr 1, 2004</time>

Well, hell, I am going to disagree with everyone here. :)

_The J2EE platform includes four deliverables: the J2EE specification, a J2EE reference implementation, a Compatibility Test Suite, and the Enterprise Java BluePrints._

The specification, reference implementation, compatibility test suite, and blueprints are all EJB-centric. The [API](http://java.sun.com/j2ee/1.4/docs/api/index.html) contains the javax.ejb.\* package. In fact any Sun Certified J2EE application server has EJB capabilities. So, going against the grain, yes, every J2EE application contains EJBs

And why not? EJBs are fun to program, highly reuseable, configurable, and obtainable. Combining that with [Core J2EE Patterns](http://tinyurl.com/yqder) and you have a well built system.

Also just because you use other non-J2EE technologies doesn't make anyone less of a java developer. So don't worry about it: a name is just a name. If you have a well designed tiered system of you own creation, so be it, wine and crackers for ALL!

Oralé,

[Dan Hinojosa](http://www.evolutionnext.com)
<hr />
####
[Lee](http://www.lwalton.co.uk/ "") - <time datetime="2004-04-06 16:03:50">Apr 2, 2004</time>

Taken this argument to it's logical conclusion would imply that unless you are using all of the features that are offered by J2EE, then you're not writing a J2EE application.

People are mistaking the criteria used to determine if an application is a J2EE apllication with the criteria used to judge if a J2EE application server is compliant.

You only have to be using a single api from the J2EE platform to be able to call your application a J2EE application.

Lee
<hr />
