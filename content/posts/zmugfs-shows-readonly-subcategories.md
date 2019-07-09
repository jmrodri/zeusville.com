---
title: 'zmugfs shows readonly (sub)categories'
date: Tue, 25 Sep 2007 04:03:09 +0000
draft: false
tags: [zmugfs python]
categories: [zmugfs]
type: post
---

I kept fighting fuse.Direntry. When I tried:

```
for n in node.get\_nodes():

     yield fuse.Direntry(n.path)

I would get NOTHING! but if I created a simple test list it would work:

```
f = \['foo', 'bar', 'path', 'cheese'\]

for i in f:

    yield fuse.Direntry(i)

It was confusing until I notice the only difference was that n.path was a unicode string while my test list were ascii stings. I thought to myself, "nah, that can't be it". But what do you know! I made this change:

```
yield fuse.Direntry(n.path.string('/').encode('ascii'))
```

Not sure if that will be the final code, IMO fuse.Direntry should work with unicode strings. But none the less, the result is a magnificent readonly view using ls and ls -l.

[![zmugfs shows ls](/img/2007/09/zmugfs_ls.png)](/img/2007/09/zmugfs_ls.png "zmugfs shows ls")


```
```