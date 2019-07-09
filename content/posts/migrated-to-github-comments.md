---
title: 'migrated to github'
date: Fri, 24 Jul 2009 01:11:14 +0000
draft: false
tags: [Linux, sm-photo-tool, zmugfs]
categories: [Linux, sm-photo-tool, zmugfs]
type: post
---


#### 
[MathStuf]( "MathStuf@gmail.com") - <time datetime="2009-07-23 21:57:22">Jul 4, 2009</time>

Why not gitorious? I package a few things that are on github (git-cola, libqinfinity, kobby) and I am only disappointed. The "bug trackers" are despicable (though I've no experience with gitorious' nothing is better than what github has). No support for attachments and patches get mangled by the wiki parser. Fork/clone/commit/push/merge request is too bureaucratic for a 2 line patch for ${LIB\_SUFFIX} support :( .
<hr />
#### 
[Richard]( "aquarichy@gmail.com") - <time datetime="2009-07-24 06:54:06">Jul 5, 2009</time>

I use gitorious and advocate it, but I'm not aware of it having any bug tracking features at all! So, you won't have any issues with those ;)
<hr />
#### 
[maa]( "ma@soundz.ch") - <time datetime="2011-01-27 06:28:38">Jan 4, 2011</time>

hi thanks for this script. i tried to set it up in ubuntu 10.10. everything installed smooth, but when i try to mount it ( zmugfs /media/smugmug/ ) i get the following error: /usr/local/lib/python2.6/dist-packages/zmugjson.py:3: DeprecationWarning: the md5 module is deprecated; use hashlib instead import md5 zmugfs:INFO: Retrieving smugmug categories, this may take several minutes... Traceback (most recent call last): File "/usr/local/bin/zmugfs", line 23, in zmugfs.main(sys.argv\[1:\]) File "/usr/local/lib/python2.6/dist-packages/zmugfs.py", line 359, in main dash\_s\_do='setsingle') File "/usr/local/lib/python2.6/dist-packages/zmugfs.py", line 67, in \_\_init\_\_ self.\_indexTree() File "/usr/local/lib/python2.6/dist-packages/zmugfs.py", line 162, in \_indexTree for cat in tree.children(): AttributeError: 'dict' object has no attribute 'children' any help would be appreciated. thanks!
<hr />
