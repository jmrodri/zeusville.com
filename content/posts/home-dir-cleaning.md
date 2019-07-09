---
title: '/home dir cleaning'
date: Mon, 03 Jul 2017 23:22:57 +0000
draft: false
tags: [Linux, Personal]
categories: [Linux, Personal]
type: post
---

After a failed Fedora 26 upgrade on Friday, I spent the day trying to recover a corrupted rpm database, missing packages, not booting into gdm. I recovered it enough to boot, but it's really in a weird state. While preparing to backup my homedir, I was go through files I no longer needed. I've been cargo culting my homedir since I started working at Red Hat in 2004. Here are the oldest files from day one:```
\[jesusr@transam ~\]$ grep "Apr 19  2004" /tmp/2004files.tzt 
-rw-r-----. 1 jesusr jesusr 153 Apr 19  2004 ./.config/nautilus/first-time-flag
-rw-r-----. 1 jesusr jesusr 82 Apr 19  2004 ./.metacity/sessions/1082391428-6426-2821178921.ms
-rw-r-----. 1 jesusr jesusr 356 Apr 19  2004 ./.metacity/sessions/1082412707-4015-1328912501.ms
-rw-r-----. 1 jesusr jesusr 82 Apr 19  2004 ./.metacity/sessions/1082413316-4377-2885991371.ms
-rw-rw-r--. 1 jesusr jesusr 226 Apr 19  2004 ./cvs/rhn/ncsu-student-projects/message-bus/rhn/LoggerTest/.classpath
-rw-rw-r--. 1 jesusr jesusr 369 Apr 19  2004 ./cvs/rhn/ncsu-student-projects/message-bus/rhn/LoggerTest/.project
-rw-rw-r--. 1 jesusr jesusr 6377 Apr 19  2004 ./cvs/rhn/ncsu-student-projects/message-bus/rhn/SqlTest/src/TestDB.java
-rwxrwxr--. 1 jesusr jesusr 5441 Apr 19  2004 ./cvs/rhn/up2date/test/PyFontify.py
-rwxrwxr--. 1 jesusr jesusr 17900 Apr 19  2004 ./cvs/rhn/up2date/test/cov2html.py
-rw-rw-r--. 1 jesusr jesusr 23499 Apr 19  2004 ./cvs/rhn/up2date/test/coverage.py
-rwxrwxr--. 1 jesusr jesusr 2043 Apr 19  2004 ./cvs/rhn/up2date/test/testRhnChannel.py
-rwxrwxr--. 1 jesusr jesusr 4648 Apr 19  2004 ./cvs/rhn/up2date/test/testTransactions.py

```Go through my homedir is like a digital archaeological dig :)