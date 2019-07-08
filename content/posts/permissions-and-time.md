---
title: 'permissions and time'
date: Thu, 11 Oct 2007 03:33:28 +0000
draft: false
tags: [python, Technology, zmugfs]
type: post
---

Tonights zmugfs update is permissions and time are now shown correctly. I defaulted the user and group to that of the user running the program (in this case me) :) And I now show the date and time correctly from the api. **Update**: by "in this case me" it doesn't mean I hardcoded my uid and gid. I used os.getuid() and os.getgid() By the way, disregard the drew and foo entries. Those are debug strings which will be removed. ![perms and time](http://zeusville.files.wordpress.com/2007/10/zmugfs_perm_time.png)