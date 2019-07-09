---
title: 'What I hate about perl'
date: Wed, 25 May 2005 21:28:04 +0000
draft: false
tags: [Java]
categories: [Java]
type: post
---

I hate the```
return something unless condition.
```This hurts my brain since I read from left to right I think return? What about the rest of the function? Oh it's unless. I prefer:

```


if (condition)

	return something;

Also, the lack of types annoys me.  I often wonder, "what am I looking at again? oh an int, no wait it's a string, hmm, actually it's all of the above, ARGH!"

I hate the grep function in perl.  That's just evil.

There is much much more, but that's it for now.


```
---
### Comments:
#### 
[Bob]( "") - <time datetime="2005-05-25 22:09:00">May 3, 2005</time>

Lack of types would be just about any "scripting" type language. At least in Perl I know what a variable looks like. I hate no sigils in front of variables (i.e. Python).
<hr />
#### 
[glenn](http://haikudojo.com "") - <time datetime="2005-05-25 23:13:45">May 3, 2005</time>

What you're saying is you dislike perl because its perl. What do you propse as a replacement for grep?
<hr />
#### 
[Brian McKendrick]( "bhmckendrick@netscape.net") - <time datetime="2005-05-26 05:11:02">May 4, 2005</time>

I used to use PERL heavily - for all types of problems - what turned me off eventually is the exact reason I went to it to begin with - it's a "Swiss-Army Chainsaw": it can do anything, but it doesn't do any one thing well. Lack of dev tools didn't help either - and the first person who says 'vi' or 'emacs' gets my foot in the ars.
<hr />
#### 
[Adam Connor](http://adamconnor.org/ "") - <time datetime="2005-05-26 08:17:11">May 4, 2005</time>

I hated unless too, when I started. It has gradually grown on me. A lot of it is just what you're used to. Perl does have types, but typing is "weak" and a source of many errors. Putting "==" instead of "eq" in the wrong place will silently create nasty bugs. ;-) Regexps were once Perl's killer advantage, but that's not true anymore. I think Ruby has most of the same advantages but a far saner syntax...
<hr />
#### 
[Luke]( "") - <time datetime="2005-06-01 09:44:02">Jun 3, 2005</time>

Java weenie :-) there's really no end to the language wars, is there? different strokes for different folks. all i know is, when i need to whip something up, i'm sure not going to write 15 java class files to do it. thppbpbt!
<hr />
