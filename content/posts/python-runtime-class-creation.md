---
title: 'python runtime class creation'
date: Sun, 18 Mar 2007 01:54:59 +0000
draft: false
tags: [Java, Technology]
categories: [Java, Technology]
type: post
---

I needed a way to dynamically create a class at runtime in python, similar to the following Java code:

`clazz = Class.forName("Image")`

`obj = clazz.newInstance()`

python has similar capabilities:

`clazz = eval("Image")`

`obj = clazz()`

But python takes it a step further. In Java, newInstance() requires a default constructor to be present, where in python I can have any constructor. For example,

```


class Image:

   def \_\_init\_\_(self, name, type):

      self.name = name

      self.type = type

clazz = eval("Image")

obj = clazz("foo", "JPG")

Another feature is that in python I can **define** a class dynamically, but I haven't tried that yet.

**UPDATE**

Michael Dehaan corrected my eval faux pas with the following code for loading classes. I wanted to get it formatted in the blog instead of in the comments:

```


# if just searching one module

# module = \_\_import\_\_(modname)

# or ...

for x in list\_of\_modules\_to\_search:

   try:

        classobj = getattr(module, classname)

        return classobj

   except AttributeError, ae:

        pass

if classobj is not None:

   inst = classobj(...)

else:

   # boom


```
```
---
### Comments:
####
[Michael DeHaan](http://michaeldehaan.net "michael.dehaan@gmail.com") - <time datetime="2007-03-19 17:48:44">Mar 1, 2007</time>

looks like that should be a break and not a return, my fault :)
<hr />
####
[Behrang](http://my.opera.com/behrangsa "behrangsa@gmail.com") - <time datetime="2007-03-18 04:35:35">Mar 0, 2007</time>

Well, In Java you can use http://java.sun.com/j2se/1.5.0/docs/api/java/lang/reflect/Constructor.html#newInstance(java.lang.Object...) to invoke any constructor you like.
<hr />
####
[Michael DeHaan](http://michaeldehaan.net "michael.dehaan@gmail.com") - <time datetime="2007-03-18 09:17:52">Mar 0, 2007</time>

eval is dangerous for the same reasons it's dangerous in perl. You probably want something like... # if just searching one module # module = \_\_import\_\_(modname) # or ... for x in list\_of\_modules\_to\_search: try: classobj = getattr(module, classname) return classobj except AttributeError, ae: pass if classobj is not None: inst = classobj(...) else: # boom
<hr />
####
[Michael DeHaan](http://michaeldehaan.net "michael.dehaan@gmail.com") - <time datetime="2007-03-18 09:18:17">Mar 0, 2007</time>

Raaargh, formatting, ah well, you get the idea :)
<hr />
