---
title: 'Horrible configure script'
date: Thu, 02 Mar 2017 03:53:40 +0000
draft: false
tags: [Linux, Technology]
type: post
---

A friend of mine was having trouble building the latest version of [R](https://cran.r-project.org/sources.html) on RHEL 6.8. The trouble was that the configure script could not verify the updated zlib. I gave him some advice, but nothing seemed to work. Typically I've solved this with a simple update of the `LD_LIBRARY_PATH`. Last night, I provisioned a RHEL 6.8 VM, downloaded the latest version of R, and tried building it myself. As expected, the configure script reported that I did not have zlib 1.2.5 installed.```
checking if zlib version >= 1.2.5... no
checking whether zlib support suffices... configure: error: zlib library and headers are required

```This is simple, just download an updated zlib, build and install. I installed zlib 1.2.11 in `/usr/local/lib64`. Re-ran configure and go the same result as above. I set `LD_LIBRARY_PATH=/usr/local/lib64:$LD_LIBRARY_PATH`, configure still complained about not finding an updated zlib. Updated zlib is installed, `LD_LIBRARY_PATH` is set. I ran `sudo ldconfig -p | grep libz`. It shows it can be found in `/usr/local/lib64`. So frustrating that everything seems to be in order and yet configure doesn't see it. My friend was using a [blog post](http://pj.freefaculty.org/blog/?p=315) to help him out, when I looked at it the author didn't see to have a problem with configure after updating zlib. What in the world is the configure script doing to determine what version of zlib we are using?```
if test "${have\_zlib}" = yes; then
  { $as\_echo "$as\_me:${as\_lineno-$LINENO}: checking if zlib version >= 1.2.5" >&5
$as\_echo\_n "checking if zlib version >= 1.2.5... " >&6; }
if ${r\_cv\_header\_zlib\_h+:} false; then :
  $as\_echo\_n "(cached) " >&6
else
  if test "$cross\_compiling" = yes; then :
  r\_cv\_header\_zlib\_h=no
else

  cat confdefs.h - <conftest.$ac\_ext
/\* end confdefs.h.  \*/

#include 
#include 
#include 
int main() {
#ifdef ZLIB\_VERSION
/\* Work around Debian bug: it uses 1.2.3.4 even though there was no such
   version on the master site zlib.net \*/
  exit(strncmp(ZLIB\_VERSION, "1.2.5", 5) < 0);
#else
  exit(1);
#endif
}

```So it's writing out a C program to verify the library. That's when I saw it.```
exit(strncmp(ZLIB\_VERSION, "1.2.5", 5) < 0);

````ZLIB_VERSION` is "1.2.11". So they are comparing the first 5 characters. **So that means "1.2.1" vs "1.2.5" and as you can see "1.2.1" is LESS THAN "1.2.5".** Well that would be a problem and never work. So I tried fixing it by changing it to use 6 characters. Well, "1.2.11" in lexicographic order is before "1.2.5". So that breaks too. I know there has to be a better way, but since this isn't my code I just wanted to it to build. I changed it to:```
exit(strncmp(ZLIB\_VERSION, "1.2.05", 6) < 0);

```Why in the world would they use `strncmp` to compare versions? Aren't there much better ways to determine libraries installed on a RHEL system? I was astounded this ever made it out to the wild.