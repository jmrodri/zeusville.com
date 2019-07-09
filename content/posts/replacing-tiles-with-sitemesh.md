---
title: 'Replacing Tiles with Sitemesh'
date: Thu, 12 Aug 2004 23:01:14 +0000
draft: false
tags: [Java]
categories: [Java]
type: post
---

Finally, a Java related post. Our project chose [Struts](http://struts.apache.org/) as our web application framework. We needed ability to specify layouts, so we used [Tiles](http://struts.apache.org/userGuide/dev_tiles.html), but it is extremely intrusive in our development process. Having to map the struts actions to tiles definitions, then making the tiles definitions, then writing the JSP pages were a pain for all of our developers. We just wanted to write our pages, then design and put in our layouts.

That's when I found [Sitemesh](http://www.opensymphony.com/sitemesh/). Sitemesh is great. It is far less invasive, actually, it's NONinvasive. I can write my JSP pages using Struts, my struts-config now maps my actions to jsp pages instead of tiles defs, and define a single layout "decorator" for our site. I'm in the process of ripping out tiles from our project and replacing it with Sitemesh. I will report on how the transition goes.
---
### Comments:
#### [Robert B]( "") - <time datetime="2004-08-13 03:48:36">Aug 5, 2004</time>

Please report your progress! I want to do this as well, with a couple of our struts/tiles apps. Seems like the right way to go.
<hr />
#### [Vinny Carpenter](http://www.j2eegeek.com/blog/ "vscarpenter@mailblocks.com") - <time datetime="2004-08-13 11:38:51">Aug 5, 2004</time>

I'll second Robert's comments above -- Please let us know how the migration goes. I am in the process of exploring a bunch of web-app frameworks for some new development and want to see how Sitemesh fits in. thanks
<hr />
