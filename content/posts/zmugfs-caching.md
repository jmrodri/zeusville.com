---
title: 'zmugfs caching'
date: Mon, 15 Oct 2007 03:55:26 +0000
draft: false
tags: [zmugfs]
categories: [zmugfs]
type: post
---

Tonight I finished a really lame in memory cache to store the image data. Basically it's a dictionary keyed by the path (filename) and the values are another dictionary with image data and timestamp. There is a new configuration entry "image.memory.cache" where you list the number of images to cache in memory, defaults to 5 (about 10MB). When it hits the max size, it removes the oldest entry in the map.

Next up is disk caching. I plan to cache some of the images on disk (in $HOME/.zmugfs/cache) I could probably also use /var/cache/zmugfs for a global install but for the first cut I'll stick with the former. This adds yet another configuration entry "image.disk.cache" specified in megabytes. Yes, I know it's lame that the value for the two caches are specified in different units. But the idea of dealing with file sizes in the memory caches versus number of entries was not appealing.

After the disk caching, the only thing left is packaging and some setup scripts to make it easier to create your configuration file.
---
### Comments:
#### 
[swiftsoles](http:// "swiftsoles@gmail.com") - <time datetime="2007-10-15 13:32:45">Oct 1, 2007</time>

What are you going to expose as the core services of zmugfs?
<hr />
#### 
[swiftsoles](http:// "swiftsoles@gmail.com") - <time datetime="2007-10-15 13:33:53">Oct 1, 2007</time>

oh yeah check out my wicked cool blog, http://swiftsoles.wordpress.com/
<hr />
