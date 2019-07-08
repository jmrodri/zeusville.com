---
title: 'rpm --repackage'
date: Wed, 18 Oct 2006 12:51:36 +0000
draft: false
tags: [Technology]
type: post
---

```
give u an example:i have amarok-1.4.3-3.FC5.i386.rpm installed on my FC5,now i want toupgrade to amarok-1.4.3-6.FC5.i386.rpm ,and i want to keep the old
version of amarok after i installed the new version

now, i can use rpm -Uvh --repackage to upgrade,and rpm command will
first repackage amarok-1.4.3-3 at /var/spool/repackage and install
amarok-1.4.3-6.FC5

# rpm -Uvh --repackage amarok-1.4.3-6.FC5.i386.rpm
# cd /var/spool/repackage
# ls

amarok-1.4.3-3.fc5.i386.rpm

understand?
```