---
title: 'rpm tip'
date: Fri, 26 Oct 2007 16:34:39 +0000
draft: false
tags: [Linux]
type: post
---

I was writing a spec file today, yes I like writing them, and wondered what macros were defined. I looked in `/etc/rpm/` but couldn't find the one I was looking for. But as we all know, man is your friend, a quick `'man rpm'` revealed `--showrc`. `rpm --showrc` will dump out the config including macros and their values.