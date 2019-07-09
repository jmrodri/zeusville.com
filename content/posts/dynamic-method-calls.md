---
title: 'dynamic method calls'
date: Wed, 14 Mar 2007 02:42:32 +0000
draft: false
tags: [sm-photo-tool]
categories: [sm-photo-tool]
type: post
---

As you may know I'm working on updating [sm-photo-tool](http://sm-photo-tool.sourceforge.net/) from [XMLPRC](http://en.wikipedia.org/wiki/XMLRPC) to [REST.](http://en.wikipedia.org/wiki/REST) I wanted similar functionality with the [REST](http://en.wikipedia.org/wiki/REST) implementation as with [XMLRPC](http://en.wikipedia.org/wiki/XMLRPC). That is I wanted to be able to do things like this:

`sm = Smugmug()`

`sm.login.withPassword("foo@foo.com", "password")`

I couldn't find a [REST](http://en.wikipedia.org/wiki/REST) library I liked probably because it's trivial as all you need is a properly formatted url. I knew it was possible to do the above with [XMLRPC](http://en.wikipedia.org/wiki/XMLRPC) in python:

`sm = ServerProxy("url")`

`sm.login.withPassword(...)`

I looked through the xmlrpclib.py and stole the \_Method implementation from it (with a slight modification):

`class _Method:`

`# some magic to bind an XML-RPC method to an RPC server.`

`# supports "nested" methods (e.g. examples.getStateName)`

`def __init__(self, send, name):`

`self.__send = send`

`self.__name = name`

`def __getattr__(self, name):`

`return _Method(self.__send, "%s.%s" % (self.__name, name))`

`def __call__(self, **args):`

`print "__name: %s" % self.__name`

`print "args: " + str(args)`

`return self.__send(self.__name, args)`

Now I can make calls to [Smugmug's](http://www.smugmug.com%3Cbr%3E%3C/a%3E) [REST api](http://smugmug.jot.com/WikiHome/REST).

`sm = Smugmug()`

`sm.smugmug.login.withPassword(EmailAddress="foo@foo.com", Password="foo")`

Next stop is to get the parsing of the XML response.