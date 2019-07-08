---
title: 'perl tip for newbies like me'
date: Mon, 23 Aug 2004 15:26:36 +0000
draft: false
tags: [Linux]
type: post
---

Need a quick way to replace a string in a lot of files? I've found the following useful:

```
perl -pi -e 's@@@g' 

```To replace c:owt with c:out in all \*.jsp files and make a backup with the extension .org use the following command:  
```
perl -pi.org -e 's@c:owt@c:out@g' \*.jsp

```