---
title: 'sm-photo-tool'
date: Tue, 18 Mar 2008 03:18:58 +0000
draft: false
tags: [Linux, python, sm-photo-tool, Technology]
categories: [Linux, python, sm-photo-tool, Technology]
type: post
---

I released a new version of [sm-photo-tool](https://sourceforge.net/project/showfiles.php?group_id=179298&package_id=207078). It's a simple script that that was originally written by [John Ruttenberg](http://rutt.smugmug.com/) wrote. I took it and packaged it in rpm form and have been maintaining it under source control (versus a forum).```
sm-photo-tool help
Usage: sm-photo-tool create gallery\_name \[options\] \[file...\]
       sm-photo-tool create\_upload gallery\_name \[options\] \[file...\]
       sm-photo-tool update \[options\]
       sm-photo-tool full\_update \[options\]
       sm-photo-tool upload gallery\_id \[options\] file...

       sm-photo-tool --help for complete documentaton
```It's create to upload an entire directory of photos to [smugmug](http://www.smugmug.com) from the command line.