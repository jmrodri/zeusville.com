---
title: 'Old overengineered project :)'
date: Sat, 24 Oct 2009 03:16:44 +0000
draft: false
tags: [Java, Linux, Technology]
categories: [Java, Linux, Technology]
type: post
---

I was looking through some old backups (~2003), and found a Java program I wrote to create thumbnails of photos for the website I was running at home. What a stupid idea that was, especially since I was running Linux at the time. There were plenty of programs that could do that conversion for me, not to mention running my own photo gallery wasn't the brightest idea either. The worst part of the code is how over engineered it was for such a simple task. I was going to delete it, but I went ahead and put the project, [PhotoResizer](http://github.com/jmrodri/PhotoResizer), up on [github](http://github.com/jmrodri/PhotoResizer) with all my other [projects](http://github.com/jmrodri). Want to see how _not_ cool it is? Sure you do, you need a good laugh right about now don't you? :)

So let's take a look at some of the over-engineering. First off, I wonder where I was in my coding when I did this. It was 2003, and I was a Java weanie. I lived and breathed Java and thought it was the greatest language ever. Six years later, I know for a fact that's just plain **WRONG**. As a Java weanie I used to think we always needed interfaces for everything "just in case" I needed to add another implementation.

So here's the [Configuration](http://github.com/jmrodri/PhotoResizer/blob/master/src/net/zeusville/core/config/Configuration.java) _interface_ :) now why the hell would I want another configuration implementation? What are the odds that I'd need more than one type of config file?

```


public interface Configuration {

    String getProperty(String key);

    int getPropertyAsInt(String key) throws NumberFormatException;

}

If you have an interface that means you probably have a concrete implementation, yep I did: 

```


package net.zeusville.core.config;

import java.util.Properties;

import java.io.FileInputStream;

import java.io.FileNotFoundException;

import java.io.IOException;

/\*\*

\* @author jmrodri

\*

\* To change the template for this generated type comment go to Window -

\* Preferences - Java - Code Generation - Code and Comments

\*/

public class PropertyConfigImpl implements Configuration {

    private Properties properties;

    public PropertyConfigImpl(String filename)

        throws InvalidConfigurationException {

        try {

            properties = new Properties();

            FileInputStream fis = new FileInputStream(filename);

            properties.load(fis);

        }

        catch (FileNotFoundException e) {

            throw new InvalidConfigurationException("Could not find \["

                    + filename + "\]", e);

        }

        catch (IOException e) {

            throw new InvalidConfigurationException("Could not read \["

                    + filename + "\]", e);

        }

    }

    /\*

\* (non-Javadoc)

\*

\* @see net.zeusville.util.Configuration#getProperty(java.lang.String)

\*/

    public String getProperty(String key) {

        return properties.getProperty(key);

    }

    public int getPropertyAsInt(String key) throws NumberFormatException {

        return Integer.parseInt(getProperty(key));

    }

}

LOL! That is certainly a lot of code to read in a .properties file. It gets better :) Because we all know that every interface and concrete implementation needs a factory or in my case a [Manager](http://github.com/jmrodri/PhotoResizer/blob/master/src/net/zeusville/core/config/ConfigurationManager.java). 

```


public class ConfigurationManager {

    private static Configuration configuration;

    public static Configuration getConfiguration() {

        if (configuration == null)

            configuration = new PropertyConfigImpl(

                    "config/PhotoResizer.properties");

        return configuration;

    }

}

Wow, that's just sad. I can't believe I actually wrote this stuff. I'm not done yet :) Like Billy Mays would say '... but that's not all, there's MORE!'

How much more could I have done to over-engineer this solution? I mean I'm just wanting to create thumbnails of a directory of pictures. Just read the list of files, and for each one convert to a configurable thumbnail size, write it out. Done right? no way José I went all out. No Java program is acceptable without **THREADS**! Don't bother getting off the floor, because what I'm about to show you next will make you laugh your @$$ off. 

Simple threads weren't good enough for this high powered solution :) I went all out and created a queue of work items with a pool of worker threads doing the conversion. No really, that's what I did. Check out the [InterThreadQueue](http://github.com/jmrodri/PhotoResizer/blob/master/src/net/zeusville/thread/InterThreadQueue.java).

Here's the run() method from the [ImageTransformer](http://github.com/jmrodri/PhotoResizer/blob/master/src/net/zeusville/ImageTransformer.java) which looks to be the guts of PhotoResizer.

```


    public void run() {

        Object item = null;

        try {

            while (keepRunning() && (item = queue.get()) != null) {

                PhotoInfo pi = (PhotoInfo) item;

                System.out.println("ImageTransformer \[" + pi.toString() + "\]");

                transform(pi);

            }

        }

        catch (InterThreadQueueTimeoutException itqe) {

            itqe.printStackTrace();

        }

    }

...

    public void transform(PhotoInfo pi) {

        createThumbNail(pi);

        createMain(pi);

    }

Not sure if I should even bother to go and clean this code up and make it simpler. Probably not, best thing to do is just scrap it, and use python or a bash script for this.

Hey you can get off the floor now. What would've caused me to write stuff like this? Simply because I was a Java weanie and that's what Java causes you to do. Try to write code that is flexible and over-engineered. Think about it, if it's a Java project and there's a database involved the team says 'Oh we need an ORM, let's use Hibernate' without first asking do we really NEED a database in the first place.

Or when writing a web ui, 'we need a web framework: Struts (yes I'm dating myself), or Seam (that's the new hotness isn't it?)' The question should probably be 'should I really use Java for my webui at all?' Answer is an obvious 'No! use Ruby or Python for it' You'll thank me later.

The next time you're about to choose a framework or any tool, ask yourself 'is this really the right tool to solve the problem?'


```
```
```
```
---
### Comments:
#### 
[partha]( "parthaa@gmail.com") - <time datetime="2009-10-24 17:40:16">Oct 6, 2009</time>

Ugh didn't keep the indents while formatiing, so using '->' for space.. You need to install Python Imaging Library :).. yum install python-imaging-devel #!/usr/bin/env python import Image import os SRC\_DIR='/home/jmrodri/data/graphics/in' DEST\_DIR='/home/jmrodri/data/graphics/out' WIDTH=64 HEIGHT=64 def thumbnail(src, dest, width, height, format = "PNG"): -> im = Image.open(src) -> im.thumbnail((width, height)) -> im.save(dest, format) for f in os.listdir(SRC\_DIR): -> thumbnail (SRC\_DIR + "/" + f, DEST\_DIR + "/" + f, WIDTH, HEIGHT)
<hr />
#### 
[Nuggets &laquo; zeusville](http://zeusville.wordpress.com/2009/10/28/nuggets/ "") - <time datetime="2009-10-28 22:13:33">Oct 3, 2009</time>

\[...\] as I stated in my Overengineered Project post., Java devs like to over engineer solutions in favor of flexibility that may or may not \[...\]
<hr />
#### 
[Robin Norwood]( "robin.norwood@gmail.com") - <time datetime="2009-10-24 00:12:47">Oct 6, 2009</time>

That's...so beautiful. It looks exactly like all other Java code ever written. More method and class definitions than lines of code. :-)
<hr />
#### 
[Adam Williamson](http://www.happyassassin.net "adamwill@shaw.ca") - <time datetime="2009-10-24 03:41:20">Oct 6, 2009</time>

"Like Billy Mays would say ‘… but that’s not all, there’s MORE!’" I believe you mean 'would have said', what with him having a severe case of dead, and all.
<hr />
#### 
[mpdehaan](http://michaeldehaan.net "michael.dehaan@gmail.com") - <time datetime="2009-10-24 08:33:04">Oct 6, 2009</time>

I hope it is using javax.foo.SomeHorriblyComplexImageLibrary versus find and and an "-exec" call to ImageMagick's "convert", otherwise I must subtract points.
<hr />
#### 
[jesus m. rodriguez](http://zeusville.wordpress.com "jmrodri@gmail.com") - <time datetime="2009-10-24 11:04:11">Oct 6, 2009</time>

Even worse, I wrote my OWN: http://bit.ly/1Oc4s7
<hr />
#### 
[mpdehaan](http://michaeldehaan.net "michael.dehaan@gmail.com") - <time datetime="2009-10-24 11:09:19">Oct 6, 2009</time>

whoa! You should go back and bicubically interpolate that :)
<hr />
#### 
[jesus m. rodriguez](http://zeusville.wordpress.com "jmrodri@gmail.com") - <time datetime="2009-10-24 19:38:25">Oct 6, 2009</time>

That's AWESOME! python rocks.
<hr />
#### 
[partha]( "parthaa@gmail.com") - <time datetime="2009-10-24 17:37:25">Oct 6, 2009</time>

#!/usr/bin/env python import Image import os SRC\_DIR='/home/jmrodri/data/graphics/in' DEST\_DIR='/home/jmrodri/data/graphics/out' WIDTH=64 HEIGHT=64 def thumbnail(src, dest, width, height, format = "PNG"): im = Image.open(src) im.thumbnail((width, height)) im.save(dest, format) for f in os.listdir(SRC\_DIR): thumbnail (SRC\_DIR + "/" + f, DEST\_DIR + "/" + f, WIDTH, HEIGHT)
<hr />
#### 
[Miroslav Suchý]( "miroslav@suchy.cz") - <time datetime="2009-10-27 07:51:14">Oct 2, 2009</time>

bash rocks even more: SRC\_DIR=’/home/jmrodri/data/graphics/in’ DEST\_DIR=’/home/jmrodri/data/graphics/out’ WIDTH=64 HEIGHT=64 for img in $ SRC\_DIR/\*.png; do $OUTPUT=\`basename $img\` convert $img -resize ${WIDTH}x$HEIGHT $OUTPUT done Anyway, the story is great. You should send it to http://thedailywtf.com/
<hr />
