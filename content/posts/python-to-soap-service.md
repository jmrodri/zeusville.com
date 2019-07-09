---
title: 'python to SOAP service'
date: Wed, 15 Nov 2006 04:32:36 +0000
draft: false
tags: [Linux, Technology]
categories: [Linux, Technology]
type: post
---

I'm working on a python to SOAP client. I'm planning on using [ZSI - The Zolera Soap Infrastructure](http://pywebsvcs.sourceforge.net/zsi.html) to implement it. This will be an interesting foray into python as I've never written anything more than a simple script, hopefully python + SOAP is better than Java + SOAP.

To make it more interesting we have python clients talking via [XMLRPC](http://www.xmlrpc.com/) to our server, which will then make a [SOAP](http://www.w3.org/TR/soap/) call. My biggest fear will be performance and SOAP service uptime.