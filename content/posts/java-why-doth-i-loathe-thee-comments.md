---
title: 'Java why doth I loathe thee'
date: Wed, 24 Jun 2009 15:07:57 +0000
draft: false
tags: [Java, Linux]
categories: [Java, Linux]
type: post
---


#### 
[Allen Halsey]( "allenhalsey@gmail.com") - <time datetime="2009-06-24 17:59:43">Jun 3, 2009</time>

Since RESTEasy is built with maven2, maybe you can download the source and rebuild it with the modified version of maven2 released with JPackage. This should cause maven2 to resolve dependencies using the already installed java libraries on your system. See Also: - http://article.gmane.org/gmane.linux.redhat.fedora.java/2941 - http://fedoraproject.org/wiki/Java/JPPMavenReadme
<hr />
#### 
[Federico]( "pedemonte@linux.it") - <time datetime="2009-06-24 12:20:17">Jun 3, 2009</time>

No, please don't! Java is alreading suffering for having been opensourced: now we have the official jdk, an openjdk for every distro (and they are different, with different behaviour), icedtea and so on. What is need less is an rpm (or deb) hell too. Java used to be a stable platform to develop on,but since it has becoming more open it is taking the same way of GNU/Linux: it is an hell to work with because it is a moving target and it is too fragmented. (Please, notice that I'm using GNU/Linux for work and fun as my only OS since 1998, but it doesn't mean that we shouldn't criticize it)
<hr />
#### 
[Andrew overholt]( "wp@overholt.ca") - <time datetime="2009-06-24 12:20:30">Jun 3, 2009</time>

This isn't the fault of "Java". It's the fault of the various communities whose unit of exchange is binary jars and not source tarballs. Re: modules -> see OSGi.
<hr />
#### 
[Devan](http://rm-rf.ca "dgoodwin@rm-rf.ca") - <time datetime="2009-06-24 12:23:55">Jun 3, 2009</time>

Java in and of itself has plenty little irritations but most of the big problems do seem to stem from it's community/culture and the way we've all been accustomed to doing things.
<hr />
#### 
[foo]( "foo@bar.com") - <time datetime="2009-06-24 13:17:42">Jun 3, 2009</time>

Java hates distros and distros hate Java. See also Windows apps, Ruby Gems, Python Eggs and so on.
<hr />
#### 
[Aaron]( "ad2clark@gmail.com") - <time datetime="2009-06-24 14:00:04">Jun 3, 2009</time>

The failing here seems to be that this is not packaged for fedora (where you could then depend on your system commons-codec). If you want better dependency management for Java, maybe look into Maven, Archiva, or Apache Ivy ?
<hr />
#### 
[mpdehaan](http://mpdehaan.wordpress.com "michael.dehaan@gmail.com") - <time datetime="2009-06-24 15:49:12">Jun 3, 2009</time>

foo, ruby gems and eggs haven't really had a distro integration problem -- they don't integrate other gems/eggs inside themselves. I knew apps did this, but the idea of libraries doing this for other libraries may be because of a LACK of a distro-agnostic system. I prefer the distro systems when they exist, but if java had egg/ez\_install/cpan/gem early on, this bad practice might not exist....
<hr />
#### 
[choeger]( "choeger@cs.tu-berlin.de") - <time datetime="2009-06-24 18:00:35">Jun 3, 2009</time>

C does not have a packaging system either. The problem is that java is cross-platform so a java program will include all bad habits from all platform ;) No, really. You should have a look at maven for compile-time dependency management and OSGi for runtime dependencies.
<hr />
