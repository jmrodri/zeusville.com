---
title: 'Sun''s Java Studio Creator'
date: Mon, 12 Apr 2004 22:07:37 +0000
draft: false
tags: [Java]
categories: [Java]
type: post
---

I downloaded the 147MB [Java Studio Creator](http://developers.sun.com/prodtech/javatools/jscreator/index.jsp) tonight to see what all the hype is about. The install goes without a hitch, it found my JDK, chose /opt/creator (where I would've put it anyway), and offered to start Creator automatically after installation.

Just to let you know what type of machine I'm working with, it's a PIII 650MHz with 512MB RAM and two - 18.4GB 15,000 RPM SCSI-3 drives running [Fedora](http://fedora.redhat.com) Core 1 Linux with JDK 1.4.2 installed and Mozilla [Firefox](http://www.mozilla.org/products/firefox/).

Back to my initial review, I choose to start Creator after the installation. I go through the wizard to create my first WebApplication (aptly named WebApplication1). I add a page (aptly named Page1.jsp). I drag over two "Component Labels" one named User Name the other Password. I add a TextField, and a Secret Field. I save the file. NOTE: The WYSIWYG view is ok especially for JSPs, but I've seen better HTML ones.

[![](http://jroller.com/resources/jmrodri/jscreator_sml.png)](http://jroller.com/resources/jmrodri/jscreator_fullscreen.png)

I'm happy with what I have, a basic JSP page with 4 "components" on it. I proceed to "Run Project". Now bear in mind I have no idea what appserver is running (assuming one that came with Creator or what's going on, I know RTFM, but if I have to RTFM to get my own hello world, I don't want to use it). The first time, it complains that it can't run Mozilla. Which is a good thing since I don't have it installed. I go the the Options menu to select my Web Browser. In the command I specify, /opt/firefox/firefox-start which is a script I have to start multiple Firefoxes. I click Run Project again, and get NOTHING. Nothing happens. No browser, no nothing. I start up Firefox, try yet again. Still nothing. I change the program to /opt/firefox/firefox (which is the main script) no change.

So at current, I've got a really basic page, with a monstrous IDE that I can't seem to connect to my Mozilla Firefox installation.

Also, it's written in SWING! With ghastly fonts. See Java Studio Creator and Eclipse below:

![](http://jroller.com/resources/jmrodri/jscreator_font.png)

![](http://jroller.com/resources/jmrodri/eclipse_font.png)

Java purists love Swing (because it's pure Java, can change look and feel, blah blah blah). I'm an SWT fan myself (no really I am). Too me, the tools I use should look like the OS, I'm running on. I don't want my IDE to look and feel like a Windows IDE on my Linux box.

Another tool tried this look and feel the same on all platforms, IBM's VisualAge. It looked the same on AIX, OS/2, and Windows. How many developers switch OSes while developing projects? I mean how many of you actually develop on multiple OSes? I would venture a guess that not many. Most Java developers either develop using Windows or using Linux. You might deploy on both, but develop on one.

I will continue to give Java Studio Creator a try, but I doubt it will win over my heart. Plus I'm determined to get it to recognize Firefox.
---
### Comments:
####
[Steve Fleming]( "ssffleming@aol.com") - <time datetime="2004-04-14 02:23:06">Apr 3, 2004</time>

Hi, I was able to get Firefox working with Creator by: 1. Main Menu: Tools/Options 2. Click System Settings on the left 3. Click Web Browser on the right and select Mozilla 4. Expand the Web Browsers node on the left 5. Select Mozilla child node of Web Browsers 6. On the right click the "..." button and edit to point to your Firefox executeable.
<hr />
####
[ahmet]( "") - <time datetime="2004-04-14 10:22:33">Apr 3, 2004</time>

honestly i like crsipy and small fonts of Swing better than the eclipse screen shot you show.. sorry :)
<hr />
