---
title: 'getting close ...'
date: Fri, 12 Oct 2007 04:32:00 +0000
draft: false
tags: [zmugfs]
categories: [zmugfs]
type: post
---

We're getting very close to releasing zmugfs 0.1, the read-only release. As you may recall on Monday I got zmugfs to [show imgdata](http://zeusville.wordpress.com/2007/10/08/zmugfs-shows-image-data/) in nautilus.[](/img/2007/10/zmugfs_imgdata.png "img data")

[![img data](/img/2007/10/zmugfs_imgdata.thumbnail.png)](/img/2007/10/zmugfs_imgdata.png "img data")

But I could only get it to work if I used the thumbnail sized imgdata. In the read() method I was logging into smugmug, reading the thumbnail imgdata, logging out of smugmug, getting the imgdata via http GET, and returning. Well, this is crazy because read gets called multiple times with different offsets. So I ended up implementing the open() and release() methods. In the open, I get the imgdata (original size) via the smugmug api and store the imgdata in an image cache (an in memory dictionary). In the read method, it now respects the offset and size attributes by reading from the image cache. Then in the release method, I delete the entry from the image cache. I know not much of a cache. :) But it solved my problem. I'm putting the cache work off a bit, not sure how to approach that yet.

Next thing I wanted to try all of the command line utils (at least the ones I've used before) to see how they react to zmugfs. I was pleasantly surprised with the result.

command

result

comment

basename

SUCCESS

 

cat

SUCCESS

 

chgrp

FAILURE

chgrp method not implemented

chmod

FAILURE

chmod method not implemented

chown

FAILURE

chown method not implemented

cp from

SUCCESS

able to copy image from smugmug using zmugfs

cp to

FAILURE

mknod not implemented

file

SUCCESS

got appropriate file type

ln -s

SUCCESS

softlink created

ls

SUCCESS

listing appears correctly

mkdir

FAILURE

mkdir method not implemented

mv

FAILURE

copy part worked; unlink not implemented

rm

FAILURE

unlink not implemented

rmdir

FAILURE

rmdir not implemented

touch

FAILURE

setattr not implemented

From a readonly perspective, it is looking great. What's left before a release you ask? Just a few things.

*   packaging

    *   write spec file

    *   figure out setup.py


*   design a logo

*   move code to zmugtools for branding purposes

*   work out image cache

That's it, once I finish those things zmugfs 0.1 will be released out into the wild! I'm really excited as this is my first ever open source project. I've submitted patches to a few things, but never anything this extensive.