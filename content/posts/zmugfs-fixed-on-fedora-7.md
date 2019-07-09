---
title: 'zmugfs fixed on Fedora 7'
date: Tue, 16 Oct 2007 15:24:48 +0000
draft: false
tags: [Linux, python]
categories: [Linux, python]
type: post
---

[Yesterday](http://zeusville.wordpress.com/2007/10/15/zmugfs-on-fedora-7/) I ran into a slight road block with simplejson. But with some playing around in the python interpreter I was able to see what the problem was with how simplejson 1.7 calls object\_hook.

Take for instance the following string:

`‘{”foobar”:”baz”,”comp”:{”key”:10},”array”:[10,20,30]}’`

simplejson 1.3 would pass the above string into the object\_hook as is. With 1.7 `{u’key’: 10}` is passed in first, followed by `{u’foobar’: u’baz’, u’array’: [10, 20, 30], u’comp’: None}`

Unfortunately, when **{u’key’: 10}** is passed in we have no context as to what this is.

I know, you all want to know what my solution was to the problem. :) Well, it was quite simple, I continue to look for the key "Categories", but if the argument does not contain it, I return the string unaltered. That's it. Now zmugfs works on Fedora Core 6 and Fedora 7.