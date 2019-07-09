---
title: 'buildr > ant > maven'
date: Sat, 13 Feb 2010 04:35:07 +0000
draft: false
tags: [Java, Technology]
categories: [Java, Technology]
type: post
---

I chose [buildr](http://buildr.apache.org) as our build tool for project candlepin, primarily because I don't care for the large amounts of XML required by [maven](http://maven.apache.org/) [pom](http://maven.apache.org/guides/introduction/introduction-to-the-pom.html) files. And [ant](http://ant.apache.org/) seems to have become passe with most Java projects.

On project [Spacewalk](https://fedorahosted.org/spacewalk/), we used [checkstyle](http://checkstyle.sourceforge.net/) to ensure the code was consistently formatted, so I wanted to do this with [candlepin](https://fedorahosted.org/candlepin/) as well. At the moment, there isn't an official checkstyle plugin for buildr, but it has the ability to create ant tasks (in Ruby). Here is my task to run checkstyle against the candlepin codebase.

```
  #

  # CHECKSTYLE task, a Buildr plugin would be better, but this is faster

  #

  task :checkstyle do

    begin

      ant('checkstyle') do |ant|

        rm\_rf 'reports/checkstyle\_report.xml'

        mkdir\_p 'reports'

        ant.taskdef :resource=>"checkstyletask.properties", :classpath=>Buildr.artifacts(CHECKSTYLE).each(&:invoke).map(&:name).join(File::PATH\_SEPARATOR)

        ant.checkstyle :config=>"buildconf/checkstyle.xml" do

          ant.formatter :type=>'plain'

          ant.formatter :type=>'xml', :toFile=>"reports/checkstyle\_report.xml"

          ant.property :key=>'javadoc.method.scope', :value=>'public'

          ant.property :key=>'javadoc.type.scope', :value=>'package'

          ant.property :key=>'javadoc.var.scope', :value=>'package'

          ant.property :key=>'javadoc.lazy', :value=>'false'

          ant.property :key=>'checkstyle.cache.file', :value=>'target/checkstyle.cache.src'

          ant.property :key=>'checkstyle.header.file', :value=>'buildconf/LICENSE.txt'

          ant.fileset :dir=>"src/main/java", :includes=>'\*\*/\*.java'

        end

      end

    end

  end

Notice the lack of XML :) that's my favorite part. I think a better integration would be to write a plugin for buildr, but for now this will suffice. Now to go fix all 800 checkstyle errors I found.


```
---
### Comments:
#### 
[Helen Val](http://fiveholiday55.blogspot.com "helenval@hotmail.com") - <time datetime="2010-03-25 14:09:01">Mar 4, 2010</time>

I've never used buildr despite years of Ant and Maven. I will check it out and take it on a spin this weekend.
<hr />
