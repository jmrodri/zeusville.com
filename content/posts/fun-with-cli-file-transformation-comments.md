---
title: 'Fun with cli file transformation'
date: Tue, 24 Mar 2015 01:55:56 +0000
draft: false
tags: [awk, cli, grep, linux, tr]
categories: [Linux, Technology]
type: post
---


#### 
[jmrodri](http://zeusville.wordpress.com/ "jmrodri@gmail.com") - <time datetime="2015-03-24 10:24:06">Mar 2, 2015</time>

Thanks for the tip Rich. looks like the package is simply called `csv` on the Fedora 21 repos.
<hr />
#### 
[rich](http:// "rich@annexia.org") - <time datetime="2015-03-24 07:06:26">Mar 2, 2015</time>

Please don't use awk to parse CSV files. It's not even remotely safe. Use a program like `csvtool` instead (it's in Fedora).
<hr />
