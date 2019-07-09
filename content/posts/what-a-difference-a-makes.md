---
title: 'What a difference a / makes'
date: Fri, 15 Jun 2007 03:17:16 +0000
draft: false
tags: [sm-photo-tool]
categories: [sm-photo-tool]
type: post
---

I've been trying to figure out why my image upload to [smugmug](http://familiarodriguez.smugmug.com) using [HTTP PUT](http://smugmug.jot.com/Uploading) wasn't working for quite some time. I always got a "connection closed" error. After looking at [this](http://inamidst.com/proj/put/put.py) example more closely I finally realized what my problem was. I forgot the freakin slash. The upload url is supposed to be http://upload.smugmug.com/filename. My code looked like this: `conn = httplib.HTTPConnection("upload.smugmug.com", 80) conn.connect() conn.request("PUT", filename, data, headers)` This obviously generates the following url: http://upload.smugmug.comXXX where XXX is the value of filename. That's just outright wrong. SIGH! But I fixed it and now my uploads work. Here's the working snippet: `conn = httplib.HTTPConnection("upload.smugmug.com", 80) conn.connect() conn.request("PUT", '/' + filename, data, headers)` Now I can get back to finishing my XMLRPC to JSON migration of [sm-photo-tool](http://sm-photo-tool.sourceforge.net/).