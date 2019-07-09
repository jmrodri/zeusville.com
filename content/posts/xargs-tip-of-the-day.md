---
title: 'xargs tip of the day'
date: Fri, 15 Feb 2008 16:22:07 +0000
draft: false
tags: [Linux]
categories: [Linux]
type: post
---

I use xargs a lot especially with find. Many times I want to pass the arguments as parameters to the command I'm trying to run with xargs usually somewhere in the middle. Today I found it :)

Time for an arbitrary example, this is completely made up to illustrate the point so don't bother with "why are you using xargs for that comments". :) So you want to find .png files that are different in /foobar/tmp and /tmp/.

`cd /foobar/tmp; find . -name '*.png' | xargs -n 1 -I imagename diff imagename /tmp/imagename`

The -I argument tells xargs to replace the string that follows -I in the command arguments with the values from standard input. This is totally cool, and beats the old way I did things which was to write a simple shell script and call that from xargs :)

There are many ways to do what I did above, but hopefully folks find this xargs tip useful.
---
### Comments:
#### [lp]( "hensgaard@netti.fi") - <time datetime="2008-02-15 14:07:21">Feb 5, 2008</time>

You can also use the -exec parameter of find like the following: `find -iname 'asdf*' -exec mv '{}' .Trash/ ';'`
<hr />
#### [Recent Links Tagged With "xargs" - JabberTags](http://www.jabbertags.com/popular/xargs "") - <time datetime="2008-10-21 01:49:40">Oct 2, 2008</time>

\[...\] public links >> xargs xargs tip of the day Saved by john32mac on Sun 19-10-2008 Useful Linux Commands 08/2008 Saved by freefoto on Sun \[...\]
<hr />
