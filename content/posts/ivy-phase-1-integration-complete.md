---
title: 'IVY phase 1 integration complete'
date: Wed, 15 Nov 2006 04:39:38 +0000
draft: false
tags: [Java, Linux]
categories: [Java, Linux]
type: post
---

I finished integrating [ivy](http://www.jayasoft.org/ivy) into our project. As you know we were developing on linux using [jpackage](http://www.jpackage.org) rpms which is a great way to install java on your linux box. But we hit a snag when we had to work in different branches with different jar dependencies. So we introduced ivy to our ant build process. I know "Why not use maven?" Because I don't like it. That's why. For an interesting comparison of maven and ivy click [here](http://www.jayasoft.org/ivy/doc/m2comparison). My next goal is to create some scripts that will allow me to specify a set of jpackage rpms, and have the ivy repository populated and autogenerate the ivy.xml files in the repo.  This will ensure when we build our rpm of java code, we develop against the same versions that we will ship with. Time for bed, been a long day.