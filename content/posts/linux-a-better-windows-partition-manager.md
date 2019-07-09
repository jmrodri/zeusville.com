---
title: 'Linux a better Windows partition manager'
date: Fri, 16 May 2008 02:34:16 +0000
draft: false
tags: [Family, Linux, Technology]
categories: [Family, Linux, Technology]
type: post
---

My inlaws were in town to help Liz through her surgery. They brought their machines to me for repair :) One of the machines had a full disk so I upgraded the 20GB to a 250GB drive.

3.  made the 20GB drive a slave

6.  installed the 250GB drive as the master

9.  booted Fedora Live CD

12.  create a partition of the same size on the new disk

15.  copy the master boot record (MBR) using dd

18.  copy the partition using dd

21.  shutdown

24.  remove power from the slave (old 20GB) drive

27.  reboot to Windows, verify things look ok.

For detailed instructions visit:

[http://www.nilbus.com/linux/disk-copy.php](http://www.nilbus.com/linux/disk-copy.php)

I stopped at the "Resizing the Partition".

The best part of all this was I never knew the power of dd, ntfsresize, and fdisk. I was originally looking for a copy of PartitionMagic or Norton Ghost. Linux is far better than any of that.

Once I finished the dd, I shutdown, and removed power from the slave drive. I rebooted and Windows came up on the new 250GB but still appeared as a 20GB drive. Now I had to resize it.

The oddest part was resizing the partition, because I couldn't wrap my head around the "delete the partition" then recreate. The delete part threw me off as I was afraid to lose the data. But it was an in memory operation so it didn't affect it. WHEW! Then I ran ntfsresize -n -s 250G /dev/sda1, then rebooted back to Windows. After a chkdsk, I was all done!

So Linux is a better Windows partition tool than Windows :)

[http://darkstar.ucd.ie/timosh/links/ntfsresize.html#cli](http://darkstar.ucd.ie/timosh/links/ntfsresize.html#cli)