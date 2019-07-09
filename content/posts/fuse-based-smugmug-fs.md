---
title: 'FUSE based smugmug FS'
date: Mon, 20 Aug 2007 01:31:27 +0000
draft: false
tags: [sm-photo-tool, Technology, zmugfs]
categories: [sm-photo-tool, Technology, zmugfs]
type: post
---

I've been using [smugmug.com](http://www.smugmug.com) to host my photos for almost 3 years now. I've been using [sm-photo-tool](http://sm-photo-tool.sourceforge.net/) to upload my pictures and I installed Fedora 7 for my wife to use to upload her pictures as well. I gave [F-spot](http://www.f-spot.org/Main_Page) a try but I'm not a big fan. Uploading to smugmug using f-spot isn't that easy either (well for more than a few photos). So I had the idea "why can't I open up a nautilus window and copy the photos to a new directory?" That's when I remembered about [FUSE](http://fuse.sourceforge.net/) but they don't have a fs built for smugmug that [I could find](http://fuse.sourceforge.net/wiki/index.php/FileSystems). So thatt's my new project to create a [FUSE](http://fuse.sourceforge.net/) based FS that connects to [smugmug.com](http://www.smugmug.com).

*   creating a new directory would create a new gallery
*   adding files into the directory will upload them to the gallery
*   deleting files removes them from smugmug
*   Linux commands like: ls, cp, mv, should all work just fine as smugmug's API has most of these capabilities.

Hopefully, I don't get bored and lose focus which is often the case with my ideas :(