---
title: 'varargs in java 1.5'
date: Sun, 18 Mar 2007 12:40:44 +0000
draft: false
tags: [Java, Technology]
type: post
---

Apparently while I was away, or should I say coding with one hand tied behind my back, [varargs](http://java.sun.com/j2se/1.5.0/docs/guide/language/varargs.html) were added to Java 1.5. It's about time. Pre 1.5 you had to do this monstrosity:```
Object\[\] arguments = {
    new Integer(7),
    new Date(),
    "a disturbance in the Force"
};

String result = MessageFormat.format(
    "At {1,time} on {1,date}, there was {2} on planet "
     + "{0,number,integer}.", arguments);
```Now if you simply add 3 dots (...) to the method declaration you can get true varargs:```
    public static String format(String pattern,
                                Object... arguments);
```which results in a much simpler usage:```
String result = MessageFormat.format(
    "At {1,time} on {1,date}, there was {2} on planet "
    + "{0,number,integer}.",
    7, new Date(), "a disturbance in the Force");
```Why did it take Sun so long to add such a useful feature? It only took 5 revisions of the language to get us this. Maybe with the recent GPLing of Java, we'll get features faster.