---
title: 'git branch in shell prompt'
date: Wed, 19 May 2010 13:52:16 +0000
draft: false
tags: [git prompt bash]
categories: [Linux, Technology]
type: post
---

I've used this prompt for quite some time but realized I never blogged about it :) As a git user I tend to work in a few branches at a time. Unlike subversion where you typically have a separate directory for each branch, with git branches update the working directory. So it is easy to get lost when you have more than one branch. Sure you can do```
git branch
```and```
git branch -r
```but this can be invasive when you could easily glance at your shell prompt. In bash (is there really any other shell?), I updated my prompt to show the current branch:```
PS1="\[\\u@\\h \\W\\$(git branch 2> /dev/null | grep -e '\\\* ' | sed 's/^..\\(.\*\\)/{\\1}/')\]\\$ "

```This make the prompt look like this:```
\[jmrodri@firebird sm-photo-tool{master}\]$ 
```