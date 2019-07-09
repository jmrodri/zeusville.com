---
title: 'disk cache for zmugfs'
date: Wed, 17 Oct 2007 02:06:22 +0000
draft: false
tags: [zmugfs]
categories: [zmugfs]
type: post
---

Tonight I wrote the disk caching logic (well most of it). zmugfs will now look in the memory cache for the imgdata, if it doesn't exist it looks in $HOME/.zmugfs/cache for the file. If it can't find it there, it does the final attempt to read it from smugmug itself.

I haven't figured out how I'm going to calculate the size of the disk cache, that's the last step to finishing that feature, otherwise it'll use whatever disk space you have.

That's it for hacking tonight. Off to watch TV.