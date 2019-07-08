---
title: 'Vonage'
date: Mon, 20 Sep 2004 23:20:20 +0000
draft: false
tags: [Java]
type: post
---

Today I got my VoIP phone adapter from [Vonage](http://www.vonage.com). I'm trying to reduce my telecommunications costs so I figured I'd give this a try. Installation was trivial, though not sure if I like the setup. The Vonage instructions said to put the phone adapter between my cable modem and my Linksys Router which seems very backwards to me. I like everything behind my router because of security.

Having the router get its IP address from the phone adapter caused my ddclient to freak out since the router now has an internal IP address instead of the external one it used to have. I'll have to fix ddclient to talk to the Motorola phone adapter OR move the phone adapter inside my router. The instructions state that if you move the phone adapter behind the router you will lose the Quality of Service feature which seems important for decent calls.

I will report back with updated news.