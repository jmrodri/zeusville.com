---
title: 'shell scripting'
date: Thu, 16 Nov 2006 15:17:33 +0000
draft: false
tags: [Linux, Technology]
categories: [Linux, Technology]
type: post
---

I'm not very good at writing shell scripts, mainly because of my ignorance to the power of the shell. Today I learned you can write a pretty complex shell script as an ssh command. For example, `ssh $REMOTE_USER$h /bin/bash << EOF [ -d $Build ] || { echo "ERROR: Build environment $Build missing" >&2 exit -1 } ... EOF` I found that cool.