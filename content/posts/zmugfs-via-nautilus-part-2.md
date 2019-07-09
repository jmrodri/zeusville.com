---
title: 'zmugfs via nautilus (part 2)'
date: Thu, 04 Oct 2007 03:53:53 +0000
draft: false
tags: [zmugfs]
categories: [zmugfs]
type: post
---

Almost a month ago I posted a screenshot of [zmugfs via nautilus](http://zeusville.wordpress.com/2007/09/09/zmugfs-through-the-eyes-of-nautilus/). Back then I was returning a hardcoded list of strings with no inode information. Last week, I got the read-only listing of categories and subcategories to work, see the ls output [here](http://zeusville.wordpress.com/2007/09/25/zmugfs-shows-readonly-subcategories/).

I thought to myself, I bet folks would love to see the new read-only functionality through nautilus. Well, prepare to be amazed and bedazzled. :) First up is a screenshot of a category showing all of the subcategories contained within. Notice all but one says "0 items", that's because I haven't figured out how to get the image count for the albums contained within yet.

[![zmugfs category](/img/2007/10/zmugfs_nautilus_category.png)](/img/2007/10/zmugfs_nautilus_category.png "zmugfs category")

The Birthday subcategory contains 9 items (all albums). So if you double click on that folder you are presented with a window showing all 9 albums in the subcategory.

[![zmugfs subcat](/img/2007/10/zmugfs_nautilus_subcategory.png)](/img/2007/10/zmugfs_nautilus_subcategory.png "zmugfs subcat")

Isn't that cool? You may be asking, "how do I know he's not just returning some random list of strings?" Well, let's [look at smugmug](http://familiarodriguez.smugmug.com/Children/117597) to see what's actually there:

[![actual smugmg subcategory](/img/2007/10/smugmug_subcategory.png)](/img/2007/10/smugmug_subcategory.png)

Next step is to get Albums to show their images and their image counts. Once that is done, I will release zmugfs 0.1 out in the wild. The following releases will add write support and possible performance enhancements.
---
### Comments:
####
[zmugfs shows image listings &laquo; zeusville](http://zeusville.wordpress.com/2007/10/06/zmugfs-shows-image-listings/ "") - <time datetime="2007-10-06 19:15:13">Oct 6, 2007</time>

\[...\] up is a subcategory containing albums. If you recall before I didn’t show the image counts, now the image counts \[...\]
<hr />
