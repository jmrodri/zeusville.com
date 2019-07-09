---
title: 'rpm --test'
date: Thu, 19 Jul 2007 19:00:25 +0000
draft: false
tags: [Linux]
categories: [Linux]
type: post
---

Often times I need to install an rpm, which I didn't get from a repo, that requires other dependencies. I used to try to install it and have it fail. But today I found --test, which is faster than doing a failed install.

So to see if you have all the needed dependencies try:

`rpm -Uvh --test foo-1.2.i386.rpm`

If everything looks good you see:

`Preparing... ########################################### [100%]`

Otherwise, you see a list of failed dependencies:

```
error: Failed dependencies:

       java-gcj-compat is needed by xml-commons-apis-1.3.03-0jpp.1.fc7.i386

       libgcj\_bc.so.1 is needed by xml-commons-apis-1.3.03-0jpp.1.fc7.i386

       rtld(GNU\_HASH) is needed by xml-commons-apis-1.3.03-0jpp.1.fc7.i386


```
---
### Comments:
####
[James Bowes](http://jbowes.dangerouslyinc.com "jbowes@gmail.com") - <time datetime="2007-07-19 19:52:54">Jul 4, 2007</time>

Also try 'yum install foo-1.2.i386.rpm'. That way you can pull in any needed deps if possible.
<hr />
