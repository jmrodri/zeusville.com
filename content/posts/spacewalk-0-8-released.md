---
title: 'Spacewalk 0.8 RELEASED!'
date: Tue, 16 Feb 2010 20:50:09 +0000
draft: false
tags: [spacewalk, Technology]
categories: [spacewalk, Technology]
type: post
---

Another Spacewalk release hits the interwebs.

**Features & Enhancements**

*   ﻿SHA256 Feature - support for packages with checksums other than MD5. Spacewalk server and proxy can serve and accept rpms with SHA256 digests, show the checksums in webUI and accept them in API calls.

*   Moved from mod\_python to mod\_wsgi on Fedora 11 and Fedora 12, which promises better performance.

*   ﻿Improved performance of SSM and API

*   and [more](https://www.redhat.com/archives/spacewalk-announce-list/2010-February/msg00000.html)

**Known Issues**

*   PostgreSQL support still does not work. We will need help with moving this forward.

*   Provider GPG key is not sometimes recognized and packages shows up as unknown Provider.

*   Documentation search does not work, other search are unaffected.

*   Cobbler 2.0 is known to work, but full tests haven't been done yet.

Congrats to the Spacewalk team for another great release!
---
### Comments:
#### [No Open Blockers &raquo; Blog Archive &raquo; Spacewalk 0.8 Released](http://noopenblockers.com/2010/02/17/spacewalk-0-8-released/ "") - <time datetime="2010-02-17 10:49:21">Feb 3, 2010</time>

\[...\] Most of the details here taken from Jesus’ post. \[...\]
<hr />
