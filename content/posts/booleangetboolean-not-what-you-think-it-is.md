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
---
### Comments:
####
[bfd]( "bfd3651@hotmail.com") - <time datetime="2003-10-10 05:55:29">Oct 5, 2003</time>

cool
<hr />
####
[Graham]( "") - <time datetime="2003-10-13 14:34:20">Oct 1, 2003</time>

it's not cool - I've been burnt by that more times than I care to mention. It should have been in java.lang.System, but they'll never move it now.
<hr />
####
[]( "") - <time datetime="2003-10-14 16:11:59">Oct 2, 2003</time>

What if what I think it does is what the javadoc says? Why would I think 'oh, the Javadoc is wrong'? Unless I didn't read it in the first place, I suppose.
<hr />
####
[Aapo Laakkonen]( "aapo.laakkonen@projectcast.com") - <time datetime="2003-10-14 16:19:46">Oct 2, 2003</time>

public static Boolean valueOf(String s), anyone? It follows the same naming pattern as String.valueOfs.
<hr />
