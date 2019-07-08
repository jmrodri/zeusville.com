---
title: 'Spacewalk 0.2!'
date: Tue, 16 Sep 2008 20:33:18 +0000
draft: false
tags: [Linux]
---


#### 
[snerd](http://motk.blogspot.com "robk@ningaui.net") - <time datetime="2008-09-16 18:55:38">Sep 2, 2008</time>

Good stuff. I'm interested in the medium to long term plans for spacewalk and it's relationship to cobbler/koan. Is there a venn-diagram yet? :)
<hr />
#### 
[Michael DeHaan](http://michaeldehaan.net/ "michael.dehaan@gmail.com") - <time datetime="2008-09-16 19:47:16">Sep 2, 2008</time>

Snerd, The current plan is for Spacewalk to utilize Cobbler/Koan for provisioning/installation as the engine for the "5.3" release for Satellite, and zeus can tell you what Spacewalk release that is. Cobbler remains seperately usable and available for those who want it, this is very much the continued idea of having "Voltronic Software" -- writing tools that can be used by multiple larger projects but also seperately. Satellite is one such robot, oVirt is another, genome is a third example, what others develop in house could be called a fourth. There is no Venn Diagram as they cause painful flashbacks to 3rd grade, but if there was, the Spacewalk circle surrounds the cobbler circle at least part way, and there are some features in cobbler that Spacewalk probably won't leverage (for example, VMware support). Things like DHCP and DNS management should be in though, as well as all the templating bits. What actually powers repo mirroring in the future Spacewalk is still TBD.
<hr />
#### 
[Devan](http://dgoodwin.dangerouslyinc.com "dgoodwin@dangerouslyinc.com") - <time datetime="2008-09-16 22:18:10">Sep 2, 2008</time>

Woooooo wooo!
<hr />
