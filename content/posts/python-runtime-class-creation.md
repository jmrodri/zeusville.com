---
title: 'python runtime class creation'
date: Sun, 18 Mar 2007 01:54:59 +0000
draft: false
tags: [Java, Technology]
type: post
---

I needed a way to dynamically create a class at runtime in python, similar to the following Java code: `clazz = Class.forName("Image") obj = clazz.newInstance()` python has similar capabilities: `clazz = eval("Image") obj = clazz()` But python takes it a step further. In Java, newInstance() requires a default constructor to be present, where in python I can have any constructor. For example,```
class Image:
   def \_\_init\_\_(self, name, type):
      self.name = name
      self.type = type

clazz = eval("Image")
obj = clazz("foo", "JPG")
```Another feature is that in python I can **define** a class dynamically, but I haven't tried that yet. **UPDATE** Michael Dehaan corrected my eval faux pas with the following code for loading classes. I wanted to get it formatted in the blog instead of in the comments:```
\# if just searching one module
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