---
title: 'Ivy dependency management'
date: Fri, 10 Nov 2006 04:13:43 +0000
draft: false
tags: [Java]
categories: [Java]
type: post
---

We started our project using [jpackage.org](http://www.jpackage.org) rpms. This works great as long as you don't have to maintain more than one branch at a time and want to upgrade the jars in those branches.

jpackage rpms install java jars in /usr/share/java/ with a version and a non-versioned symlink. e.g. struts-1.2.9.jar and struts.jar. The utilities offered in jpackage-utils are quite handy for Linux java development, we used build-jar-repository to build our lib directories during build time. This is nice as you can say build-jar-repository --symbolic project/libdir/ hibernate3 struts ...

But the problem occurs when you need to upgrade struts for branch B, but still need to build branch A using an older version of struts.

Many of you are probably saying, well [maven](http://maven.apache.org/) does this. But I'm not fan of maven, I'm just not so don't even go there. We use [ant](http://ant.apache.org/) as our build tool and it is quite capable, except we wanted maven's dependency management of jars. We don't have the time to gut our build system to replace it with maven. One of our engineers suggested [Ivy](http://www.jayasoft.org/ivy). Ivy ROCKS! I created a rudimentary repo with the jars we need, and got our ant build file connected to ivy fairly quickly. I want to retain some of the simplicity we had with our jpackage setup, so I'm writing some utility scripts. Yes I know these scripts aren't portable, but I don't much care as I work on Linux, and deploy on Linux.

I'll keep folks posted on how this goes. But if you're an [Ant](http://ant.apache.org/) shop and despise maven, consider using [Ivy.](http://www.jayasoft.org/ivy)
---
### Comments:
#### [Carlos Sanchez](http://www.jroller.com/page/carlossg "carlos@apache.org") - <time datetime="2006-11-21 14:13:15">Nov 2, 2006</time>

You should try the Maven Ant tasks http://maven.apache.org/ant-tasks.html
<hr />
