---
title: 'Replacing Tiles with Sitemesh'
date: Thu, 12 Aug 2004 23:01:14 +0000
draft: false
tags: [Java]
type: post
---

Finally, a Java related post. Our project chose [Struts](http://struts.apache.org/) as our web application framework. We needed ability to specify layouts, so we used [Tiles](http://struts.apache.org/userGuide/dev_tiles.html), but it is extremely intrusive in our development process. Having to map the struts actions to tiles definitions, then making the tiles definitions, then writing the JSP pages were a pain for all of our developers. We just wanted to write our pages, then design and put in our layouts.

That's when I found [Sitemesh](http://www.opensymphony.com/sitemesh/). Sitemesh is great. It is far less invasive, actually, it's NONinvasive. I can write my JSP pages using Struts, my struts-config now maps my actions to jsp pages instead of tiles defs, and define a single layout "decorator" for our site. I'm in the process of ripping out tiles from our project and replacing it with Sitemesh. I will report on how the transition goes.