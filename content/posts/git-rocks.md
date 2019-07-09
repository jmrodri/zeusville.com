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
---
### Comments:
#### [Jeremy Katz](http://katzj.livejournal.com "katzj@redhat.com") - <time datetime="2008-09-18 22:54:05">Sep 4, 2008</time>

It's unfortunate that the learning curve for git is what it is, because you're right, it is very awesome once you learn how to use it effectively. Another cool thing you may not have seen yet with git is interactive commits (git commit or git add with the --interactive flag)
<hr />
#### [Andy Price](http://andrewprice.me.uk "andy@andrewprice.me.uk") - <time datetime="2008-09-19 02:48:46">Sep 5, 2008</time>

My learning curve was pretty shallow to get to git: CVS (basics) -> Subversion -> Bazaar -> Git. So it can be pretty easy to learn, depending on where you're coming from and, of course, how much pressure you're under to learn it. I started learning Git by keeping my university assignments in it so it was a pretty gradual thing where I used it every day. P.S. When you say "whoas" do you mean "woes"? Sorry, I'm a pedant :)
<hr />
#### [Devan](http://dgoodwin.dangerouslyinc.com "dgoodwin@dangerouslyinc.com") - <time datetime="2008-09-19 08:00:25">Sep 5, 2008</time>

Took me awhile to write down all the stuff I needed to remember for daily workflow but once I had that to work with and a basic understanding of how things work, git really started to shine. "Learn your tools" is right.
<hr />
#### [Paul W. Frields](http://paul.frields.org/ "stickster@gmail.com") - <time datetime="2008-09-19 11:31:09">Sep 5, 2008</time>

Jesus -- thank you, thank you, thank you for posting this! I admit I rarely have a ton of time to cruise through the docs, but you just answered one of the exact questions I've been asking myself recently. Please feel free to keep blogging git hints when you have time, I love it!
<hr />
#### [Adrian LIkins](http://www.adrianlikins.com "adrian@likins.com") - <time datetime="2008-09-19 15:50:15">Sep 5, 2008</time>

You should start a "stupid git tricks" fedora planet meme. Or maybe a "post your git cheat sheet"\[1\] meme. \[1\] It seems like everyone has one...
<hr />
#### [Toshio Kuratomi]( "a.badger@gmail.com") - <time datetime="2008-09-19 16:08:13">Sep 5, 2008</time>

git has a lot of cool features like all DVCS's . The one major problem that I have with it is the horrible mess that is git branches. Branching was one thing that I felt subversion was a huge improvement over cvs and it's disappointing to see git retrograde in this regard. I'd tell everyone to use bzr, which has a very sane branching model except that its speed is nothing to write home about when compared to git. :-(
<hr />
#### [Jay Dobies]( "jdob@redhat.com") - <time datetime="2008-09-23 16:57:41">Sep 2, 2008</time>

I'm still at the "this is making my head hurt" stage. Glad to hear I'm not alone and that it gets better. :)
<hr />
