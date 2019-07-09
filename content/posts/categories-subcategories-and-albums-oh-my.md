---
title: 'categories, subcategories, and albums OH MY!'
date: Sat, 25 Aug 2007 00:29:44 +0000
draft: false
tags: [zmugfs]
categories: [zmugfs]
type: post
---

Now that I have [mkdir](http://zeusville.wordpress.com/2007/08/23/mkdir-works-in-zmugfs/) partially working, I need to figure out the use case for it. [SmugMug](http://www.smugmug.com) has the notion of [categories](http://smugmug.jot.com/WikiHome/1.2.0/smugmug.categories.get) and [albums](http://smugmug.jot.com/WikiHome/1.2.0/smugmug.albums.get). Here is how I plan on making it work. Since categories can contain [subcategories](http://smugmug.jot.com/WikiHome/1.2.0/smugmug.subcategories.get) but albums can not, I will make the categories the top level tree of directories with the leaf directory becomes an album.

Let's walk through an example. Let's assume you mount smugmug in /mnt/smugmug. If you want to create a "Samuel Birthday 2007" album in the Children category and in the Birthday subcategory you would do the following:

`mkdir -p "/mnt/smugmug/Children/Birthday/Samuel Birthday 2007"`

at that point if the categories don't exist they will be created as will the album.

The one edge case I see here is if you want a Birthday album under the Children category. Should I allow directories to have both? maybe I can store metadata about them somewhere. For now, I'll leave that use case out until I see a good way of handling it.
---
### Comments:
#### 
[zmugfs through the eyes of nautilus &laquo; zeusville](http://zeusville.wordpress.com/2007/09/09/zmugfs-through-the-eyes-of-nautilus/ "") - <time datetime="2007-09-09 20:28:25">Sep 0, 2007</time>

\[...\] FUSE and about filesystem calls has been extremely interesting. I started out trying to get mkdir to work and realized I’m better off getting the read only part done \[...\]
<hr />
#### 
[flaw in original idea &laquo; zeusville](http://zeusville.wordpress.com/2007/08/31/flaw-in-original-idea/ "") - <time datetime="2007-08-31 00:17:58">Aug 5, 2007</time>

\[...\] in original idea 31 08 2007 There’s a flaw in my thinking with categories, subcategories, and albums. mkdir -p /Category/Subcategory/Album will pass in each path separately. So I don’t have any \[...\]
<hr />
