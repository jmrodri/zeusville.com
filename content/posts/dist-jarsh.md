---
title: 'dist-jar.sh'
date: Thu, 23 Nov 2006 05:00:03 +0000
draft: false
tags: [Java, Technology]
categories: [Java, Technology]
type: post
---

Tonight I created a shell-script to allow our developers to add jar files to our [Ivy](http://www.jayasoft.org/ivy) repo. As java on Linux developers, we use rpm packaged jars (see [jpackage.org](http://www.jpackage.org)). The shell-script will take in a host and a list of rpms and/or jars. For the rpms, it will extract the jar files to a cpio archive, then copy the jars to the repo. So for example, if you download antlr-2.7.6.noarch.rpm from jpackage and want to add the jars to your ivy repo, it's as simple as this: `./dist-jar.sh --host ivyrepo.foobar.com antlr-2.7.6.noarch.rpm` DONE! Next step is to make this a little less dependent on our internal buildsystem so that it is useful for other ivy users. Happy Thanksgiving everyone.