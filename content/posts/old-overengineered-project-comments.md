---
title: 'Old overengineered project :)'
date: Sat, 24 Oct 2009 03:16:44 +0000
draft: false
tags: [Java, Linux, Technology]
categories: [Java, Linux, Technology]
type: post
---


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
