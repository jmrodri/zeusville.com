---
title: 'mkdir works in zmugfs'
date: Fri, 24 Aug 2007 03:19:04 +0000
draft: false
tags: [zmugfs]
categories: [zmugfs]
type: post
---

It took a bit of work, but I got mkdir to create a new category (album) on [smugmug](http://www.smugmug.com). I mounted my [zmugfs](http://sm-photo-tool.svn.sourceforge.net/viewvc/sm-photo-tool/trunk/zmugfs/src/zmugfs.py?revision=48&view=markup) on /tmp/fuse. I ran the following commands:

![commands](http://zeusville.files.wordpress.com/2007/08/commands.png)

And they showed up in [smugmug](http://www.smugmug.com). Still a lot of bugs, but I'm happy with the progress.

![albums in smugmug](http://zeusville.files.wordpress.com/2007/08/mkdir.png)
---
### Comments:
####
[categories, subcategories, and albums OH MY! &laquo; zeusville](http://zeusville.wordpress.com/2007/08/24/categories-subcategories-and-albums-oh-my/ "") - <time datetime="2007-08-24 20:29:49">Aug 5, 2007</time>

\[...\] subcategories, and albums OH MY! 24 08 2007 Now that I have mkdir partially working, I need to figure out the use case for it. SmugMug has the notion of categories \[...\]
<hr />
