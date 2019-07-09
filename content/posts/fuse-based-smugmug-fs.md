---
title: 'FUSE based smugmug FS'
date: Mon, 20 Aug 2007 01:31:27 +0000
draft: false
tags: [sm-photo-tool, Technology, zmugfs]
categories: [sm-photo-tool, Technology, zmugfs]
type: post
---

I've been using [smugmug.com](http://www.smugmug.com) to host my photos for
almost 3 years now. I've been using [sm-photo-tool](http://sm-photo-tool.sourceforge.net/)
to upload my pictures and I installed Fedora 7 for my wife to use to upload
her pictures as well. I gave [F-spot](http://www.f-spot.org/Main_Page) a try
but I'm not a big fan. Uploading to smugmug using f-spot isn't that easy either
(well for more than a few photos).

So I had the idea "why can't I open up a nautilus window and copy the photos
to a new directory?" That's when I remembered about [FUSE](http://fuse.sourceforge.net/)
but they don't have a fs built for smugmug that
[I could find](http://fuse.sourceforge.net/wiki/index.php/FileSystems). So
that's my new project to create a [FUSE](http://fuse.sourceforge.net/) based FS
that connects to [smugmug.com](http://www.smugmug.com).

* creating a new directory would create a new gallery
* adding files into the directory will upload them to the gallery
* deleting files removes them from smugmug
* Linux commands like: ls, cp, mv, should all work just fine as smugmug's API
  has most of these capabilities.

Hopefully, I don't get bored and lose focus which is often the case with my
ideas :(

---
### Comments:

#### [zmugfs 0.1 RELEASED! &laquo; zeusville](http://zeusville.wordpress.com/2007/10/31/zmugfs-01-released/ "") - <time datetime="2007-10-31 23:59:16">Oct 3, 2007</time>

\[...\] 0.1 RELEASED! 31 10 2007 After two and half months of development, I
would like to announce the first release of zmugfs (yes, the Halloween release) \[...\]

---
#### [Don MacAskill](http://blogs.smugmug.com/don/ "don@smugmug.com") - <time datetime="2007-08-19 22:58:44">Aug 0, 2007</time>

This is such a cool idea! I'm the CEO & Chief Geek at SmugMug, and would love
to see this. Definitely drop us a note if there's any help we can give, or if
you need the API extended in some way. Our API forum is the place to be, if
you haven't checked it out already: http://www.dgrin.com/forumdisplay.php?f=25
Thanks, and good luck!

---
#### [zmugfs tree created &laquo; zeusville](http://zeusville.wordpress.com/2007/08/20/zmugfs-tree-created/ "") - <time datetime="2007-08-20 00:09:03">Aug 1, 2007</time>

\[...\] tree created 20 08 2007 Based on my earlier “announcement”, zmugfs svn
repo created: \[...\]

---
#### [python&#8217;s default argument values &laquo; zeusville](http://zeusville.wordpress.com/2007/09/24/pythons-default-argument-values/ "") - <time datetime="2007-09-24 23:11:02">Sep 1, 2007</time>

\[...\] 24 09 2007 I’ve been trying to track down a bug for a couple days now
with zmugfs. I’m caching the tree structure returned by smugmug.users.getTree.
Here’s my Node \[...\]

---
#### [samir](http://bootwala.net "jeitob@yahoo.com") - <time datetime="2010-10-15 14:22:29">Oct 5, 2010</time>

hello. have you made progress on this front? will this FUSE fs work with osx?
i am extremely disappointed that all of the cloud image storage sites do not
offer any filesystem connection, and furthermore no sync ability. currently im
using dropbox to store images, and was hoping i could do bi-directional sync
with them to smugmug like i did with picasaweb. thx!

----
