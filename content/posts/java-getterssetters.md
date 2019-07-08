---
title: 'Java getters/setters'
date: Wed, 25 Jul 2007 13:18:31 +0000
draft: false
tags: [Java]
type: post
---

One of the things I dislike about Java are having to write getters and setters. In this discussion on [Sun's Developer Forum](http://forum.java.sun.com/thread.jspa?forumID=31&threadID=280669), someone was wanting to know how to auto generate getters and setters. They seem to frustrate a few folks to the point where some want to ignore them altogether:

> i gave up on gets/sets about 2weeks after my lecturer introduced them to us :/ if a var can be modified, then make it public. Though adding a get/set method does provide encapsulation, it also requires more typing, bloats code and is also a fraction slower. Sometimes gets/sets serve a purpose, but most of the time theyre just a waste of time. Its quite funny watching a newbie programmer start writing a class, they identify the classes required attributes, then write 200lines of gets and sets before they even consider tackling the 'hard' bit\[s\] of the class :\] rob,

While I find not using getters and setters a bit extreme, I don't like the fact that I need an IDE to auto generate getters and setters. What would really be nice is if Java could "just know" when it finds a member variable at runtime with no getter/setter, it's implied. It's a lot like the default constructor behaves. For example, it should suffice to be able to write the following User class, and be able to call it's getters and setters. `public class User { private String name; private int age; }` Then I can say: `User u = new User(); u.setName("fname lname"); assertEquals("fname lname", u.getName());` If I want to override the default functionality of Java, then I can create the getter or setter like I do today.