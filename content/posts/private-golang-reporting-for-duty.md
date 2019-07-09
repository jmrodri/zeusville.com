---
title: 'Private Golang, reporting for duty'
date: Sun, 14 Aug 2016 23:59:37 +0000
draft: false
tags: [Go, Golang, Java, python, Technology]
categories: [Go, Golang, Java, python, Technology]
type: post
---

Many modern programming languages have a mechanism for controlling the visibility of members and methods. Most of the languages use keywords like private and public.

Java and C++ use `public`, `private`, and `protected`. Ruby also uses keywords: `private`, and `protected`.

Python on the other hand uses convention to control visibility, prefixing your methods with `_` or `__`. Even then it's more of a suggestion in Python as you can call it anyway. There is nothing to prevent it from actually being called from other code. It's an understanding among Python developers that if there is an underscore you shouldn't call it.

Go also has no keyword to control visibility. What no keyword? There has to be something? Maybe it uses `_` like python? Nope that won't do anything. Then what would Go use to control visibility? Go uses a very simple syntax, capitalization.

CAPITALIZATION? What? Yes, that's correct. A simple capital letter makes the member or method public. Lowercase member, methods are private.

```
// GetName is a public method of User struct

func (u \*User) GetName() string {

  return u.name

}

// nickName is a private method of User struct

func (u \*User) nickName() {

  // do something

}

The same logic applies to members. Given the following example struct, Foo is public and bar is private:

```
type Example struct {

  Foo string

  bar string

}

So if you want to make your Go methods or members private, just start them with a lowercase letter. Want others to use it, capitalize it.


```
```
---
### Comments:
####
[Links 15/8/2016: Linux 4.8 RC2, Glimpses at OpenMandriva Lx 3.0 | Techrights](http://techrights.org/2016/08/15/glimpses-at-openmandriva-lx-3-0/ "") - <time datetime="2016-08-15 19:59:51">Aug 1, 2016</time>

\[…\] Private Golang, reporting for duty \[…\]
<hr />
