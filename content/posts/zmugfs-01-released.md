---
title: 'zmugfs 0.1 RELEASED!'
date: Thu, 01 Nov 2007 03:59:08 +0000
draft: false
tags: [python, zmugfs]
categories: [python, zmugfs]
type: post
---

After [two and half months](http://zeusville.wordpress.com/2007/08/19/fuse-based-smugmug-fs/) of development, I would like to announce the first release of zmugfs (yes, the Halloween release) :). I was inspired to write this program when I got my wife, Elizabeth, to try out Fedora to import her digital pictures because "it just works in Fedora". But uploading using the website was a bit lame, so I thought, "it would be cool if you could open up nautilus and see your pictures, then copy them to the folder to upload them".

That's how [zmugfs](http://zeusville.wordpress.com/category/technology/python-technology/zmugfs/) was born. What the heck is [zmugfs](http://zeusville.wordpress.com/category/technology/python-technology/zmugfs/)? It's a [FUSE](http://fuse.sourceforge.net/)\-based filesystem written entirely in python (my new favorite language) which connects to your account on [smugmug.com](http://www.smugmug.com/) using their [JSON apis](http://smugmug.jot.com/API).

[**DOWNLOAD** zmugfs here](http://sourceforge.net/project/showfiles.php?group_id=205794)!

zmugfs requires [zmugjson](http://soureforge.net/project/showfiles.php?group_id=205794) and [fuse-python](http://sourceforge.net/project/showfiles.php?group_id=121684&package_id=231951) to work, actually requires a paid [smugmug.com](http://www.smugmug.com) account to be useful.

Installing on Fedora 7:

*   yum install fuse-python

*   download the f7 rpms of zmugfs and zmugjson

*   configure it with your username and password ($HOME/.zmugfs/zmugfsrc or /etc/zmugfs/zmugfs.conf)

*   /usr/bin/zmugfs <mount directory>

*   DONE!

Installing on Fedora Core 6:

*   yum install fuse-python (from the extras repo)

*   download the rpms of zmugfs and zmugjson

*   configure it with your username and password ($HOME/.zmugfs/zmugfsrc or /etc/zmugfs/zmugfs.conf)

*   /usr/bin/zmugfs <mount directory>

*   DONE!

Or if not a Fedora user, and [you should be](http://fedoraproject.org/get-fedora), try the tarballs.

Here's a sample config file:

`smugmug.username=zmuggy@somewhere.org`

`smugmug.password=zmuggys_password`

`# number of images to cache`

`image.memory.cache=5`

`# amount of image data to cache in megabytes`

`# 50 ~ 25 images`

`image.disk.cache=50`
---
### Comments:
####
[zmugfs roadmap &laquo; zeusville](http://zeusville.wordpress.com/2008/01/09/zmugfs-roadmap/ "") - <time datetime="2008-01-09 10:52:04">Jan 3, 2008</time>

\[...\] 9 01 2008 I released zmugfs 0.1 on October 31st, 2007, but I haven’t done anything else with it since then. I’m overdue \[...\]
<hr />
####
[Devan](http://dgoodwin.dangerouslyinc.com "dgoodwin@dangerouslyinc.com") - <time datetime="2007-11-01 08:14:23">Nov 4, 2007</time>

Congrats zeus! If only I wasn't a flickr user... :)
<hr />
####
[James Bowes](http://jbowes.dangerouslyinc.com "jbowes@redhat.com") - <time datetime="2007-11-01 09:17:23">Nov 4, 2007</time>

Buy me a smugmug account and I'll test it for you =D
<hr />
####
[Petri Savolainen]( "petri.savolainen@iki.fi") - <time datetime="2007-12-03 06:05:18">Dec 1, 2007</time>

Hi, thanks for writing this! This was an itch I had for a long time, I am glad someone actually went ahead and wrote some code :-) I will definitely test the code (on Xubuntu & perhaps Debian 4.0) & hopefully I'll be able to pitch in as well at some point.
<hr />
####
[Russianspi]( "dan@dananddalaina.com") - <time datetime="2008-05-18 15:12:10">May 0, 2008</time>

Hey - I created .debs using Alien. They install and run fine using Ubuntu 8.04, but I had to install python-simplejson also to make it work. E-mail if you want debs to post.
<hr />
