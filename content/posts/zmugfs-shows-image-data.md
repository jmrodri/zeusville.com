---
title: 'zmugfs shows image data'
date: Mon, 08 Oct 2007 04:22:58 +0000
draft: false
tags: [zmugfs]
categories: [zmugfs]
type: post
---

Success. I got zmugfs to show image data in nautilus. It is a horribly inefficient algorithm but it works. I do the following:

*   login to smugmug
*   getUrls for imageid
*   httpget image from above url
*   return imgdata

I know EWW! :) But it worked! ![img data](http://zeusville.files.wordpress.com/2007/10/zmugfs_imgdata.png) That's cool and all, but I bet what would be really cool is to open the file up in [GIMP](http://www.gimp.org). ![gimp](http://zeusville.files.wordpress.com/2007/10/zmugfs_gimp.png) How's that for coolness! It's 12:18am EDT, I need to get to bed because I have to get up at 6:30am to get the kiddies ready for school. If all goes well, I should be able to get zmugfs 0.1 released by next week.