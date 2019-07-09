---
title: 'what tag is this commit in?'
date: Fri, 17 May 2013 14:48:39 +0000
draft: false
tags: [Linux, Technology]
categories: [Linux, Technology]
type: post
---

Thanks to [jbowes](http://blog.repl.ca/) for saving me time with git. I had a commit and wanted to find out what tag it was in. I tended to do the opposite, given a tag is this commit in it. And boy did I do it the hard way:

```


git checkout TAG

git checkout -b TAG # assuming there wasn't one already

tig # search for the commit in the list

That was cumbersome and a bit error prone. Now with a simple command I can find the tag more easily.

```


git describe --contains COMMIT\_SHA


```
```
---
### Comments:
#### [jhaaps]( "haaja@iki.fi") - <time datetime="2013-05-18 07:24:35">May 6, 2013</time>

Alternative way is: git tag --contains COMMIT\_SHA
<hr />
