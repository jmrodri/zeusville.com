---
title: 'Java why doth I loathe thee'
date: Wed, 24 Jun 2009 15:07:57 +0000
draft: false
tags: [Java, Linux]
categories: [Java, Linux]
type: post
---

I'm working on a new project that will be written in Java and have a JSON REST-like api. For the project we're investigating [RESTEasy](http://www.jboss.org/resteasy/). I proceed to download the zip file (ugh) and look inside. That's when I remember why I loathe Java so much.

`[jesusr@... ]$ unzip -v ~/Download/resteasy-jaxrs-1.1.GA-all.zip | awk '{print $8}' | grep "\.jar$"`

`resteasy-jaxrs-1.1.GA/lib/activation-1.1.jar`

`resteasy-jaxrs-1.1.GA/lib/apache-mime4j-0.6.jar`

`resteasy-jaxrs-1.1.GA/lib/async-http-jbossweb-1.1.GA.jar`

`resteasy-jaxrs-1.1.GA/lib/async-http-servlet-3.0-1.1.GA.jar`

`resteasy-jaxrs-1.1.GA/lib/async-http-tomcat6-1.1.GA.jar`

`resteasy-jaxrs-1.1.GA/lib/commons-codec-1.2.jar`

`resteasy-jaxrs-1.1.GA/lib/commons-httpclient-3.1.jar`

`resteasy-jaxrs-1.1.GA/lib/commons-logging-1.1.1.jar`

`resteasy-jaxrs-1.1.GA/lib/FastInfoset-1.2.7.jar`

`resteasy-jaxrs-1.1.GA/lib/guice-1.0.jar`

`resteasy-jaxrs-1.1.GA/lib/jackson-core-asl-1.0.1.jar`

`resteasy-jaxrs-1.1.GA/lib/jackson-jaxrs-1.0.1.jar`

`resteasy-jaxrs-1.1.GA/lib/jackson-mapper-asl-1.0.1.jar`

`resteasy-jaxrs-1.1.GA/lib/javassist-3.6.0.GA.jar`

`resteasy-jaxrs-1.1.GA/lib/jaxb-api-2.1.jar`

`resteasy-jaxrs-1.1.GA/lib/jaxb-impl-2.1.10.jar`

`resteasy-jaxrs-1.1.GA/lib/jaxrs-api-1.1.GA.jar`

`resteasy-jaxrs-1.1.GA/lib/jboss-common-core-2.2.10.GA.jar`

`resteasy-jaxrs-1.1.GA/lib/jboss-logging-spi-2.0.5.GA.jar`

`resteasy-jaxrs-1.1.GA/lib/jbosscache-core-3.0.3.GA.jar`

`resteasy-jaxrs-1.1.GA/lib/jcl-over-slf4j-1.5.8.jar`

`resteasy-jaxrs-1.1.GA/lib/jettison-1.1.jar`

`resteasy-jaxrs-1.1.GA/lib/jgroups-2.6.7.GA.jar`

`resteasy-jaxrs-1.1.GA/lib/jsr250-api-1.0.jar`

`resteasy-jaxrs-1.1.GA/lib/jta-1.1.jar`

`resteasy-jaxrs-1.1.GA/lib/jyaml-1.3.jar`

`resteasy-jaxrs-1.1.GA/lib/mail-1.4.jar`

`resteasy-jaxrs-1.1.GA/lib/resteasy-atom-provider-1.1.GA.jar`

`resteasy-jaxrs-1.1.GA/lib/resteasy-cache-core-1.1.GA.jar`

`resteasy-jaxrs-1.1.GA/lib/resteasy-guice-1.1.GA.jar`

`resteasy-jaxrs-1.1.GA/lib/resteasy-jackson-provider-1.1.GA.jar`

`resteasy-jaxrs-1.1.GA/lib/resteasy-jaxb-provider-1.1.GA.jar`

`resteasy-jaxrs-1.1.GA/lib/resteasy-jaxrs-1.1.GA.jar`

`resteasy-jaxrs-1.1.GA/lib/resteasy-multipart-provider-1.1.GA.jar`

`resteasy-jaxrs-1.1.GA/lib/resteasy-spring-1.1.GA.jar`

`resteasy-jaxrs-1.1.GA/lib/resteasy-yaml-provider-1.1.GA.jar`

`resteasy-jaxrs-1.1.GA/lib/scannotation-1.0.2.jar`

`resteasy-jaxrs-1.1.GA/lib/sjsxp-1.0.1.jar`

`resteasy-jaxrs-1.1.GA/lib/slf4j-api-1.5.8.jar`

`resteasy-jaxrs-1.1.GA/lib/slf4j-simple-1.5.8.jar`

`resteasy-jaxrs-1.1.GA/lib/stax-api-1.0.jar`

Why oh why do Java projects have to include **every** library they use? I already have a version of commons-codec on my machine. Why do I need yet another? As a Linux user, I'm used to downloading software that requires the libraries it needs to be installed, either by manually building the required libraries or using RPM to install the software and its dependencies. Java is in desperate need of an RPM like dependency manager for deploying software because having to include a copy of every single library and version you need is down right ridiculous.

I know many will argue that 'we certify the project against version X of library Y, any other version might break'. That's a bigger problem in the Java community where they commonly break ABI/API compatibility even in point releases. For example, a library called jfreechart once removed an entire package in a point release: 0.9.20 to 0.9.21. This required our code to be recompiled against the newest one. That is just silly and shouldn't be allowed. In the C world that would get you banned from writing C libraries.

</rant>