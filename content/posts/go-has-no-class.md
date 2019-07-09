---
title: 'Go has no class'
date: Sat, 04 Jun 2016 03:53:23 +0000
draft: false
tags: [Go, Golang, Java, Technology]
categories: [Go, Golang, Java, Technology]
type: post
---

Coming from [Java](http://openjdk.java.net/), [Python](https://www.python.org/), and [Ruby](https://www.ruby-lang.org/en/), I'm used to working with objects and methods. Go doesn't have classes but it does have structs that you can add methods to it.

In Java, you would typically do the following:

```
public class User {

  private String name;

  public User(String name) {

    this.name = name;

  }

  // method with return value

  public String getName() {

    return this.name;

  }

  // method with argument

  public void setName(String name) {

    this.name = name;

  }

  // method with argument and return value

  public int argWithReturn(String anarg) {

    return anarg.length();

  }

}

In Go you would use a struct.

```
type User struct {

    name string

}

The weirdest part is that you don't define the methods in the struct block. How do you add methods to the User struct? Simply create a function and add `(u *User)` to it.

```
func (u \*User) GetName() string {

    return u.name

}

func (u \*User) SetName(nm string) {

    u.name = nm

}

func (u \*User) ArgWithReturn(anarg string) int {

    return len(anarg)

}

Whoa, that's strange. Why does `GetName` return a `*User` type? It doesn't, the return type is defined at the end of the definition. So `GetName` actually returns a `string`. The `(u *User)` is how you tell Go these methods are attached to the `User` struct.

I think I'll look either into packages or argument parsing.


```
```
```