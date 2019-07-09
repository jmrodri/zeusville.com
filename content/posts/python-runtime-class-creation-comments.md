---
title: 'python runtime class creation'
date: Sun, 18 Mar 2007 01:54:59 +0000
draft: false
tags: [Java, Technology]
categories: [Java, Technology]
type: post
---


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
