---
title: 'selfless isn''t always good'
date: Fri, 14 Sep 2007 13:21:17 +0000
draft: false
tags: [Technology, zmugfs]
categories: [Technology, zmugfs]
type: post
---

Last night I posted a little blurb about [python's self](http://zeusville.wordpress.com/2007/09/13/self/). My bud [dgoodwin](http://dgoodwin.dangerouslyinc.com/) agreed with me, but after reading the reason it exists we both felt much better about having to use it. According to the [General Python FAQ](http://www.python.org/doc/faq/general/#why-must-self-be-used-explicitly-in-method-definitions-and-calls) there's a pretty good reason to have it:

> The idea was borrowed from Modula-3. It turns out to be very useful, for a variety of reasons.
>
> First, it's more obvious that you are using a method or instance attribute instead of a local variable. Reading self.x or self.meth() makes it absolutely clear that an instance variable or method is used even if you don't know the class definition by heart. In C++, you can sort of tell by the lack of a local variable declaration (assuming globals are rare or easily recognizable) -- but in Python, there are no local variable declarations, so you'd have to look up the class definition to be sure. Some C++ and Java coding standards call for instance attributes to have an m\_ prefix, so this explicitness is still useful in those languages, too.
>
> Second, it means that no special syntax is necessary if you want to explicitly reference or call the method from a particular class. In C++, if you want to use a method from a base class which is overridden in a derived class, you have to use the :: operator -- in Python you can write baseclass.methodname(self, ). This is particularly useful for \_\_init\_\_() methods, and in general in cases where a derived class method wants to extend the base class method of the same name and thus has to call the base class method somehow.
>
> Finally, for instance variables it solves a syntactic problem with assignment: since local variables in Python are (by definition!) those variables to which a value assigned in a function body (and that aren't explicitly declared global), there has to be some way to tell the interpreter that an assignment was meant to assign to an instance variable instead of to a local variable, and it should preferably be syntactic (for efficiency reasons). C++ does this through declarations, but Python doesn't have declarations and it would be a pity having to introduce them just for this purpose. Using the explicit "self.var" solves this nicely. Similarly, for using instance variables, having to write "self.var" means that references to unqualified names inside a method don't have to search the instance's directories. To put it another way, local variables and instance variables live in two different namespaces, and you need to tell Python which namespace to use.

Hopefully you won't curse python for being selfish next time.
---
### Comments:
#### [James Bowes](http://jbowes.dangerouslyinc.com "jbowes@redhat.com") - <time datetime="2007-09-14 13:06:01">Sep 5, 2007</time>

You were just having a Java relapse. Love each language for its own strengths and faults, man.
<hr />
