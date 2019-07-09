---
title: 'Vonage'
date: Mon, 20 Sep 2004 23:20:20 +0000
draft: false
tags: [Java]
categories: [Java]
type: post
---

Today I got my VoIP phone adapter from [Vonage](http://www.vonage.com). I'm trying to reduce my telecommunications costs so I figured I'd give this a try. Installation was trivial, though not sure if I like the setup. The Vonage instructions said to put the phone adapter between my cable modem and my Linksys Router which seems very backwards to me. I like everything behind my router because of security.

Having the router get its IP address from the phone adapter caused my ddclient to freak out since the router now has an internal IP

address instead of the external one it used to have. I'll have to fix ddclient to talk to the Motorola phone adapter OR move the phone adapter inside my router. The instructions state that if you move the phone adapter behind the router you will lose the Quality of Service feature which seems important for decent calls.

I will report back with updated news.
---
### Comments:
#### 
[Cliff](http://www.jroller.com/page/Cliff "") - <time datetime="2004-09-21 10:34:27">Sep 2, 2004</time>

Interesting. Now you got me scared. I just signed up for Lingo which is a more economical Vonage clone. I got my hardware last Friday but I can't hook it up until I pick up my cable modem today. I hope I don't have similar issues. Let me know how everything works out.
<hr />
#### 
[Muness Alrubaie](http://muness.blogspot.com "muness@gmail.com") - <time datetime="2004-09-21 12:43:09">Sep 2, 2004</time>

I use the Vonage phone adapter behind my router. Works fine, though I do limit my bandwith usage when on the phone for better phone quality.
<hr />
