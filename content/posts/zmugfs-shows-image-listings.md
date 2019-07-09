---
title: 'zmugfs shows image listings'
date: Sat, 06 Oct 2007 23:13:09 +0000
draft: false
tags: [zmugfs]
categories: [zmugfs]
type: post
---

Yesterday I started implementing the image listings for the albums. I finished it up today. Here are the latest screenshots.

First up is an ls listing of the Album which appears on the filesystem as a directory (click the image to see a larger view, and yes that is Obi-wan in the background). The permissions aren't quite right for the images, but that's a minor change to the stat structure.

[![zmugfs shows ls listing of images](http://zeusville.files.wordpress.com/2007/10/zmugfs_ls_imgs.png)](http://zeusville.files.wordpress.com/2007/10/zmugfs_ls_imgs.png "zmugfs shows ls listing of images")

Next up is a subcategory containing albums. If you [recall before](http://zeusville.wordpress.com/2007/10/03/zmugfs-via-nautilus-part-2/) I didn't show the image counts, now the image counts appear.

![zmugfs shows image counts now](http://zeusville.files.wordpress.com/2007/10/zmugfs_naut_cat_imgcnt.png)

Finally, you can see an album with the list of images and their file sizes. Since this only returns the filename information nautilus can't render the previews. Still this is cool stuff, well in my opinion it's cool stuff :)

![zmugfs image list](http://zeusville.files.wordpress.com/2007/10/zmugfs_naut_imglist.png)