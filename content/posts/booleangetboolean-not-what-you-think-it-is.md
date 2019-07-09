---
title: 'Boolean.getBoolean not what you think it is'
date: Thu, 09 Oct 2003 14:47:32 +0000
draft: false
tags: [Java]
categories: [Java]
type: post
---

In Java there is a Boolean object which has a nice static method called getBoolean that takes in a String. It returns a primitive boolean. So one would think that the following would print true.

...

String foo = "true";

System.out.println( "Value \[" + Boolean.getBoolean( foo ) + "\]" ); ...

But getBoolean() does not translate a String into a boolean primitive. It gets the boolean value of a SYSTEM PROPERTY.

From the Javadoc:

Returns true if and only if the system property named by the argument exists and is equal to the string "true".