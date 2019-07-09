---
title: 'Windows is still a pain'
date: Wed, 17 Mar 2010 15:24:21 +0000
draft: false
tags: [Linux, Technology]
categories: [Linux, Technology]
type: post
---

So I'm setting up a new [Windows 7](http://windows.microsoft.com/en-us/windows7/products/what-is) machine for my inlaws. This time it's a new [Dell](http://www.dell.com) preinstalled with Windows 7, which is great I don't have to actually install the OS. But Windows still sucks to setup, first I had to figure out how to copy the data from the old machine to the new. In Linux, I would simply rsync the homedirs from the old to the new machine. Thankfully Windows 7 had a "[Windows Easy Transfer](http://windows.microsoft.com/en-US/windows7/products/features/windows-easy-transfer)" program (rsync is still easier) :)

After all of the data and user accounts were copied over, Windows Easy Transfer presented me with a list of all the applications I should probably installed based on the settings it found in the data transfer. This was extremely useful, and also where the pain starts. In Linux ([Fedora](http://fedoraproject.org/)), I would simply setup the appropriate yum repos, then yum install firefox, google-chrome, nvidia-kmod, etc. With Windows I have to go to each of the vendors sites and download their custom setup program. The worst is when you have a few applications to install and they each want you to reboot after each one.  Only 15 more applications to install now :(

</windows-rant>
---
### Comments:
#### [Michael DeHaan](http://michaeldehaan.net/ "michael.dehaan@gmail.com") - <time datetime="2010-03-17 11:55:26">Mar 3, 2010</time>

I'm really impressed with Mac's "copy settings from your old mac" tool, that can use either a Time Machine backup or a Firewire connection. Anaconda doing that would be nice, though I question whether video and such would actually work with old X-configs and what other dragons are lurking.
<hr />
#### [Stephen Smoogen]( "smooge@gmail.com") - <time datetime="2010-03-17 13:27:28">Mar 3, 2010</time>

Hey I am doing this for my parents right now. I wish they ahd a tool like the Mac because it would make so much easier. One thing I did like was that it nags me to set up backups for the box.
<hr />
