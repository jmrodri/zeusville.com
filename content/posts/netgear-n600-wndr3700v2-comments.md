---
title: 'Netgear N600 WNDR3700v2'
date: Wed, 25 May 2011 01:57:34 +0000
draft: false
tags: [Linux, Technology]
---


#### 
[Mike McCune](http://suds.org "mmccune@gmail.com") - <time datetime="2011-12-11 14:35:06">Dec 0, 2011</time>

found it handy to run it in an endless loop so you can repeat tests and not have to muck with the server: #!/bin/bash while : do nc -v -l 2222 > /dev/null done
<hr />
