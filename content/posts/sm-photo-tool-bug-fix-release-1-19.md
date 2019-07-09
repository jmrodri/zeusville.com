---
title: 'sm-photo-tool bug fix release - 1.19'
date: Sat, 31 Oct 2009 01:48:28 +0000
draft: false
tags: [python, sm-photo-tool, Technology]
categories: [python, sm-photo-tool, Technology]
type: post
---

[sm-photo-tool](http://github.com/jmrodri/sm-photo-tool/) had a problem where it would no longer upload pictures to your [smugmug.com](http://smugmug.com) account, a bug of this magnitude pretty much renders a photo uploader useless :) I fixed the upload issue and at the same time switched it from using a HTTP POST with multipart encoded data to HTTP PUT. Uploads are now FASTER! You can download version 1.19 here: [http://github.com/jmrodri/sm-photo-tool/downloads](http://http://github.com/jmrodri/sm-photo-tool/downloads)