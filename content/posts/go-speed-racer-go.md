---
title: 'Go! Speed Racer Go!'
date: Thu, 25 Aug 2016 03:56:32 +0000
draft: false
tags: [Go, Golang, python, sm-photo-tool, Technology]
categories: [Go, Golang, python, sm-photo-tool, Technology]
type: post
---

I finally reached a point where I could start running the go version of `sm-photo-tool`. I finished the option validation for the `list` command. While I was testing it I noticed how much faster the Go version felt. Here are the python vs Go versions of the commands. The python version took 80 milliseconds to run the validation of parameters and print out the error message. This is expected, you have to start the python VM (and if not precompiled, the code would need to be compiled). In this test, the code was precompiled.```
$ time sm-photo-tool list invalid blah
ERROR: valid options are \['album', 'galleries'\]

real	0m0.080s
user	0m0.059s
sys	0m0.021s

```Ok so how fast is the Go version? My guess was half the time, 40ms. I was way off. Try 6ms. SIX! That's amazing to do the exact same amount of work.```
$ time ./sm-photo-tool list invalid blah
ERROR: valid options are \[album galleries\]

real	0m0.006s
user	0m0.001s
sys	0m0.005s

```