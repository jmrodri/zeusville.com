---
title: 'Java getters/setters'
date: Wed, 25 Jul 2007 13:18:31 +0000
draft: false
tags: [Java]
categories: [Java]
type: post
---

One of the things I dislike about Java are having to write getters and setters. In this discussion on [Sun's Developer Forum](http://forum.java.sun.com/thread.jspa?forumID=31&threadID=280669), someone was wanting to know how to auto generate getters and setters. They seem to frustrate a few folks to the point where some want to ignore them altogether:

> i gave up on gets/sets about 2weeks after my lecturer introduced them to us :/
>
> if a var can be modified, then make it public. Though adding a get/set method does provide encapsulation, it also requires more typing, bloats code and is also a fraction slower.
>
> Sometimes gets/sets serve a purpose, but most of the time theyre just a waste of time.
>
> Its quite funny watching a newbie programmer start writing a class, they identify the classes required attributes, then write 200lines of gets and sets before they even consider tackling the 'hard' bit\[s\] of the class :\]
>
> rob,

While I find not using getters and setters a bit extreme, I don't like the fact that I need an IDE to auto generate getters and setters. What would really be nice is if Java could "just know" when it finds a member variable at runtime with no getter/setter, it's implied. It's a lot like the default constructor behaves.

For example, it should suffice to be able to write the following User class, and be able to call it's getters and setters.

`public class User {`

`private String name;`

`private int age;`

`}`

Then I can say:

`User u = new User();`

`u.setName("fname lname");`

`assertEquals("fname lname", u.getName());`

If I want to override the default functionality of Java, then I can create the getter or setter like I do today.
---
### Comments:
#### [F.Baube]( "fbaube@saunalahti.fi") - <time datetime="2007-07-25 10:49:32">Jul 3, 2007</time>

Check out how Groovy handles this. It's quite sensible and unbloatly.
<hr />
#### [James Bowes](http://jbowes.dangerouslyinc.com "jbowes@redhat.com") - <time datetime="2007-07-25 12:42:55">Jul 3, 2007</time>

Alternatively, use a language that has properties.
<hr />
#### [Dantelope](http://arkoftecture.blogspot.com/ "dantelope@donotreply.com") - <time datetime="2007-07-25 14:26:12">Jul 3, 2007</time>

I fail to see how this is an issue. If you want non-private access to member variables, then make your member variables non-private. The risk you run is, if later you want to override the set/get behavior, then you need to refactor. However, this risk is easily mitigated as refactoring using an IDE (or any good search/replace tool) is a fast and trivial task. What's the point of hiding your variables from callers if you want them to access it directly without programmatic intervention? Your request seems purely semantic. `public class User { public String firstName; public String lastName; } public class Caller { public void function() { User u = getCurrentUser(); System.out.println( "Hello, " + u.firstName + " " + u.lastName ); } }` Post-refactor: `public class User { private String firstName; private String lastName; public String getFirstName() { return .... } public String getLastName() { return .... } } public class Caller { public void function() { User u = getCurrentUser(); System.out.println( "Hello, " + u.getFirstName() + " " + u.getLastName() ); } }`
<hr />
#### [Dantelope](http://arkoftecture.blogspot.com/ "dantelope@donotreply.com") - <time datetime="2007-07-25 14:27:20">Jul 3, 2007</time>

Wow, my formatting really got messed up there, sorry. :(
<hr />
#### [Monty]( "montechristos@gmail.com") - <time datetime="2007-07-25 12:24:05">Jul 3, 2007</time>

You don't want to create getters and setters for ALL of your fields. What you can use is aspect oriented programming (with annotations on the fields you want to create getters/setters for) to 'auto'-generate getters/setters
<hr />
#### [Kirk](http://www.kodewerk.com "kirk@kodewerk.com") - <time datetime="2007-07-26 01:16:54">Jul 4, 2007</time>

1) Don't discount the power of encapsualtion, 2) Getters and setters always get inlined so there is no performance penalty
<hr />
#### [atleta](http://www.atleta.hu "spam@atleta.hu") - <time datetime="2007-07-26 09:12:13">Jul 4, 2007</time>

Hmm... the code blocks should keep the indentation to make code samples readable.
<hr />
#### [atleta](http://www.atleta.hu "spam@atleta.hu") - <time datetime="2007-07-26 09:11:08">Jul 4, 2007</time>

You have to mark somehow what variables you want to make public by getters/setters. A private variable is private by default. You may give access by adding a getter **and/or** a setter. Most of the times getters and setters are not OK from OO design point of view. So if you have to write a lot of them then you may have misdesigned your classes. Sometimes you need them of course and I think that using a getter/setter pair instead of pure public access is till better because you still have the chance to change the implementation behind the property. Anyway, what you ask for still makes sense and it could be correctly implemented using annotations. Say: `public class User { @Get @Set private String name; @Get private int age; }` And you don't even need to modify the language or the compiler for this you just need an annotation processor (a byte code post processor that generates the getters and the setters as needed).
<hr />
#### [partha]( "parthaa@gmail.com") - <time datetime="2007-07-30 22:01:20">Jul 1, 2007</time>

Huge commentary on this -> http://www.javaworld.com/javaworld/jw-09-2003/jw-0905-toolbox.html
<hr />
#### [partha]( "parthaa@gmail.com") - <time datetime="2007-07-30 22:05:31">Jul 1, 2007</time>

That being said though Dantelope's comment got me thinking....... This probably only an issue for public API's that you want to preserve forever for backward compatibility :).. If all the code is in-house only, i.e. code never to be extended by the outside world may be we can just make them public variables... Hmm.......
<hr />
#### [amardeep sachan]( "amardeep_sachan@yahoo.com") - <time datetime="2008-02-18 08:59:40">Feb 1, 2008</time>

why am i using getter and setter
<hr />
#### [Christophe Bismuth]( "christophe.bismuth@gmail.com") - <time datetime="2009-05-10 08:01:18">May 0, 2009</time>

Hi, I don't agree with you about performance. I've made a test in my Java project: 1. Use get/set everywhere even inside declaring classes: 2,500 s execution time, 2. Use get/set only from the outside and in declaring classes only when they wrap around some business logic: 2,078 s execution time. It means that solution 2 was 16,8% faster than solution 1 on a very fast JUnit test. I think it could be really more relevant on a longer test. Besides, I think that solution 2 is smarter because you write code as you need it, isn't it? That's not a problem of inlined code, I think that it's a problem a call stack. Hope it helps, Chris
<hr />
#### [coffy]( "coffy.sk@gmail.com") - <time datetime="2010-11-12 10:37:52">Nov 5, 2010</time>

There is maybe solution for you. (us). http://projectlombok.org/
<hr />
