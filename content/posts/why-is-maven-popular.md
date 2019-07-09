---
title: 'Why is maven popular?'
date: Wed, 24 Jan 2007 16:28:55 +0000
draft: false
tags: [Java, Technology]
categories: [Java, Technology]
type: post
---

So why is it that among Java folks [maven](http://maven.apache.org) is so popular? The pom.xml is an abomination, it's is difficult to maintain and I've had simpler [ant](http://ant.apache.org/) build files. I know maven has dependency resolution which you can get with ant using [Ivy](http://www.jaya.free.fr/ivy/). Maven supports multiple projects, but that can be done with ant as well.

So what is it that makes maven so popular? skeptical minds want to know.
---
### Comments:
#### [David Rabinowitz](http://www.davidrabinowitz.com/ "davidrab@gmail.com") - <time datetime="2007-01-25 04:57:41">Jan 4, 2007</time>

Here are the reason for my transition to maven: \* Transitive dependencies - there is no need to locate and download various libraries and to save them in the source control. \* immediate build file - I don't need to take care of the prepare, delete, etc questions. I don't need to think of the trivial prepare-compile-test-package-deploy cycle with all the minor steps that needed. No copy paste between ant files (I know you can import, it's not the same). Almost everything can be done with configuration - I tell maven what I want to do, and it just does it. \* IDE project generation - I can download any project, and immediately create project for my eclipse. \* No more makefile! Ant is basically an impressive makefile, and is suitable for many tasks. However, for building software projects it's not the best tool now.
<hr />
#### [freeeeringtones](http://www.thehotstop.info "free-ringtones@thehotstop.info") - <time datetime="2007-08-18 00:50:22">Aug 6, 2007</time>

popular free ringtones www.thehotstop.info signature...
<hr />
