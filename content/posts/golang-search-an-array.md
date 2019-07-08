---
title: 'Golang: search an array'
date: Mon, 08 Aug 2016 03:57:18 +0000
draft: false
tags: [Go, Technology]
type: post
---

Go is a pretty awesome language, typed, C-like, fast. I'm porting one of my python applications to Go. Searching an array isn't as simple as it is in python though. In Python you can use `in` or `not in`:```
if self.args\[1\] not in self.valid\_options:
    print("ERROR: valid options are %s" % self.valid\_options)
    sys.exit(1)

```Go doesn't have membership operators, so you have to search the string for what you want. Then you get the index and see if it actually exists:```
i := sort.SearchStrings(lc.valid\_options, args\[1\])
if i >= len(lc.valid\_options) ||
  i < len(lc.valid\_options) && lc.valid\_options\[i\] != args\[1\] {

  fmt.Printf("ERROR: valid options are %v\\n", lc.valid\_options)
  os.Exit(1)
}

```