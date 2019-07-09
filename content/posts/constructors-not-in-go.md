---
title: 'Constructors? Not in Go'
date: Wed, 10 Aug 2016 02:40:04 +0000
draft: false
tags: [Go, Golang, Technology]
categories: [Go, Golang, Technology]
type: post
---

If you've used any object-oriented language in the past decade, [C++](https://en.wikipedia.org/wiki/C%2B%2B), [Java](https://en.wikipedia.org/wiki/Java_(programming_language)), [Python](https://en.wikipedia.org/wiki/Python_(programming_language)), [Ruby](https://en.wikipedia.org/wiki/Ruby_(programming_language)), [C#](https://en.wikipedia.org/wiki/C_Sharp_(programming_language)), you are used to defining a class and each having its own constructor. Here's a sample in Java and Python, respectively.

```
public class User {

    private String username;

    public User(String name) {

        username = name

    }

    // ...

}

```
class User(object):

    def \_\_init\_\_(self, name):

        self.username = name

Previously, I wrote about [Go having no class](https://zeusville.wordpress.com/2016/06/03/go-has-no-class/). Go uses structs. I covered how to write a struct and add methods to it. But now how do you create one? Let's continue with the user example from above. In Go, we'd create a user struct:

```
type User struct {

    username string

}

Ok that was easy. But what about the constructor? Go doesn't use constructors as you are accustomed. Go will basically initialize everything to their ZERO value, i.e. ints are 0, strings are empty. structs will have their members set to their respective zero values. Let's look at the User example above.

```
u := User{}

This creates the User u instance with the username set to the zero value for strings, "".

Sometimes the zero value isn't enough. Sometimes you want to pass in values you know you need for that particular instance. That's pretty simple too, again let's look at the User struct:

```
u : User{"joeuser"}

This will set the username to `joeuser`. What if the struct had more attributes? You can either specify all the values in order or by name and value. Let's add the `age` attribute to the User struct.

```
type User struct {

    username string

    age int

}

Initialize both by passing all the values:

```
u := User{"joeuser", 30}

Alternatively, we can initialize the username and leave the age to be it's default zero value.

```
u := User{username: "joeuser"}

But what about something more complex than a two field User object? Since Go doesn't have constructors, you have to create what I like call a "pseudo constructor", basically a method that returns the initialized struct.

```
func NewUser(name string, age int) \*User {

    // do whatever work you need to do

    // calculate fields, set defaults, etc.

    if age < 18 {

        fmt.Println("user is a minor")

    }

    return &User{name, age}

}

The name can be anything, I like to use NewStructName as a convention to make it easier to see what they are for.

While Go doesn't have constructors, there are still three ways you can "construct" objects:

*   using the zero values

*   using the {} to pass in the values to the struct

*   creating a construction function to build the struct

Now "Go" and construct some objects.


```
```
```
```
```
```
```
```
```
---
### Comments:
#### [Links 11/8/2016: Linux 4.6.6, KDE Kirigami UI Framework | Techrights](http://techrights.org/2016/08/11/kde-kirigami-ui-framework/ "") - <time datetime="2016-08-11 07:14:49">Aug 4, 2016</time>

\[…\] Constructors? Not in Go \[…\]
<hr />
