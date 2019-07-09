---
title: 'Cause for aneurysm'
date: Mon, 04 Oct 2010 16:39:38 +0000
draft: false
tags: [Java]
categories: [Java]
type: post
---

I think working with [maven](http://maven.apache.org/pom.html#Build) is going to give me an aneurysm. Say you want to compile your code for Java 1.6. Seems like a simple task. In most build systems it is actually trivial, except in [maven](http://maven.apache.org/pom.html#Build). In [ant](http://ant.apache.org/), you add two attributes to the `javac` tag.```
<javac destdir="${target.dir}/classes"
           ...
           source="1.6"
           target="1.6"
           ...>

```In [buildr](http://buildr.apache.org), it's even simpler.```
compile.options.target = '1.6'

```But what about maven you ask? Yes you knew it was coming. It's completely obnoxious what you have to do.```
  <build>
    ...
    <plugins>
      ...
      <plugin>
        <groupId>org.apache.maven.plugins</groupId>
        <artifactId>maven-compiler-plugin</artifactId>
        <configuration>
          <source>1.6</source>
          <target>1.6</target>
        </configuration>
      </plugin>
    </plugins>
  </build>

````pom.xml` files are just painful. [Maven](http://maven.apache.org) I **hate** you.