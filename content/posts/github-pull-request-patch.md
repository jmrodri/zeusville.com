---
title: 'github pull request patch'
date: Thu, 01 Nov 2012 22:14:17 +0000
draft: false
tags: [git, Linux, Technology]
type: post
---

Nifty way to test out a github pull request:```
git checkout master
# Check out your master branch
curl https://github.com/octocat/Spoon-Knife/pull/25.patch | git am
# Grab the patch generated by a pull request and feed it into a new commit

```[https://help.github.com/articles/using-pull-requests](https://help.github.com/articles/using-pull-requests)