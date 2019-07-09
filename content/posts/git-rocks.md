---
title: 'git rocks'
date: Fri, 19 Sep 2008 02:17:03 +0000
draft: false
tags: [Linux, Technology]
categories: [Linux, Technology]
type: post
---

Some time last year, I worked on a project that used [git](http://git.or.cz/) as its scm. Coming from [CVS](http://www.nongnu.org/cvs/) and [Subversion](http://subversion.tigris.org/), I HATED git. I couldn't do the most basic things like revert a file deal with branches, etc. I blamed git for my whoas woes. I quickly dismissed git as a fad and something only kernel engineers should use.

Then back in April we set out to open up [Spacewalk](https://hosted.fedoraproject.org/spacewalk/), a few of the other engineers suggested we use git over Subversion. I figured why the hell not, so that's what we went with. I've now realized that last year when I blamed git for my whoas, it wasn't git at all. It was me. A [friend of mine](http://rkbloom.net/) once said, "learn your tools", and that's what I've been doing with git. I'm more and more impressed with it now that I use it day in and day out.

Tonight, I became acquainted with _git-stash_. Man that is one cool little command. I had 2 changes going on and need to get them out of the way to do a _git pull_. I simply did a `git-stash save "foobar stuff"`, then updated with git pull, and restored my stuff with `git-stash apply stash@{1}`. This stuff ROCKS!

If you're a [CVS](http://www.nongnu.org/cvs/) or [Subversion](http://subversion.tigris.org/) user I suggest you try out [git](http://git.or.cz/). At first it will truly annoy you :) but stick with it and you'll learn to love it. Personally, I think the better way is to play with it, walk away for a while, then come back and give it a second go.