---
title: 'Where are all the SWT applications?'
date: Fri, 02 Apr 2004 15:51:04 +0000
draft: false
tags: [Java]
categories: [Java]
type: post
---

Why aren't there more SWT applications? Eclipse has become extremely popular (partly because of its use of SWT giving it native look and feel as well as speed). So again, where are the SWT applications?
---
### Comments:
####
[Hani Suleiman]( "") - <time datetime="2004-04-02 16:16:09">Apr 5, 2004</time>

There are very few, for some very good reasons: - SWT programming goes against many standard java paradigms, it's awkard and clunky and makes swing look smooth and elegant - Swing performance is no longer an issue. Compare IDEA to Eclipse - SWT is not cross-platform, and developers on non-win32 platforms are immediately turned off since they're very much second class citizens - With LAF's like jgoodies and winlaf, you get the benefits of a native LAF without any of the awkwardness.
<hr />
####
[]( "") - <time datetime="2004-04-02 18:23:34">Apr 5, 2004</time>

Hani said it very well. I tried to write an SWT application and I hated it.
<hr />
####
[Glen Stampoultzis](http://www.jroller.com/page/gstamp "") - <time datetime="2004-04-03 00:30:08">Apr 6, 2004</time>

I mostly agree with you Hani but there is one area where Swing doesn't cut it. SWT will always be better at letting you take advantage of the operating system since it's much closer to the metal. For the 80-90% of people that don't need to take advantage of OS specific stuff then stick with Swing - it's flexible and after you get over the learning curve not too hard to use.
<hr />
####
[Keith Lea]( "keith@cs.oswego.edu") - <time datetime="2004-04-03 03:12:42">Apr 6, 2004</time>

Glen, what OS specific stuff can you do with SWT that you can't do with Swing? All I've seen that I can think of is that SWT can get an icon for a mime type, and embed a browser window, and you can do both of those in other ways (like JNIWrapper, or pure JNI).
<hr />
####
[Adrian](http://jroller.com/page/aspinei/ "") - <time datetime="2004-04-03 04:28:43">Apr 6, 2004</time>

For a possible answer see http://www.jroller.com/page/aspinei/20040403#re\_where\_are\_all\_the
<hr />
####
[Glen Stampoultzis]( "") - <time datetime="2004-04-03 07:41:47">Apr 6, 2004</time>

Keith... I think I'll just take back what I said. I looked at JNI wrapper and they've done a very good job of providing all this stuff. I had thought some of these things were problematic because swing uses lightweight components but going through the demos has proved me wrong. I will say though that swing still does a pretty poor job at emulating the native L&F in most cases. That's something that can be fixed but Sun seems to be taking their time with this.
<hr />
####
[Jesus M. Rodriguez](http://www.jroller/page/jmrodri "jmrodri@nc.rr.com") - <time datetime="2004-04-03 14:37:18">Apr 6, 2004</time>

Adrian had the best answer. SWT is still young and currently tools are being built using the Eclipse platform.

Though I agree with Hani that SWT goes against standard Java paradigms. SWT still offers native look and feel as does Swing. I've tried Swing apps, they still feel much slower than SWT or native Windows & GTK apps. With SWT, I get drag and drop, with Swing it's a kludge. With SWT, I get **native** look and feel, with Swing I get _emulated_ look and feel.

And the recent tab changes in Eclipse, I do not consider those look and feel (like Swing does), but that is simply "theming" which is the ability to change your entire system to have a particular theme. Can Swing take advantage of my GNOME themes? The answer is NO. Can SWT? YES!

Hani said that SWT is hard to program. I've found that in order to make an application user friendly, there will be more work put on the developer. So using Swing might be easier to develop, it doesn't offer the experience a user would expect from a native application.
<hr />
####
[Partha]( "") - <time datetime="2004-04-03 17:41:12">Apr 6, 2004</time>

I agree with Jesus on "With SWT, I get drag and drop, with Swing it's a kludge. With SWT, I get native look and feel, with Swing I get emulated look and feel."

A good example of this is Eclipse vs NetBeans. Both run on Mac OS X.. ( I would love to post a pictures here but I am unable to do so, I dunno how post images here on jroller...). Eclipse looks like a native Mac OS X application, with the menus exactly appearing where they should on a mac. It seems as if the app is built using cocoa..

While in Netbeans there are 2 layers of Menubars. One that appears on the top of the application (as it does in all Mac OS X Apps) and one that swing adds inside its applications.. it really seems emulated as opposed to native. The net result, the app's LAF just not appealing (rather appalling (: )... I don't have much experience developing SWT apps so I can't comment on that.

Anyway if one likes Swing Style coding but wants to use SWT they can always use SwingWt ->http://swingwt.sourceforge.net/
<hr />
####
[Mike Cogan](http://www.revisingscbcd.co.uk "michael.cogan@revisingscbcd.co.uk") - <time datetime="2004-04-04 03:48:51">Apr 0, 2004</time>

I prefer SWT to Swing and from my experience Business Users do as well. I also prefer web front ends to fat client applications and I think Swing does a very good job at making users want web front ends too or it makes them want MS technology.
<hr />
####
[martin](http://weblogs.javahispano.org/page/mperez "") - <time datetime="2004-04-05 02:04:38">Apr 1, 2004</time>

I haven't read all the posts but it took my attention this :

_And the recent tab changes in Eclipse, I do not consider those look and feel (like Swing does), but that is simply "theming" which is the ability to change your entire system to have a particular theme. Can Swing take advantage of my GNOME themes? The answer is NO. Can SWT? YES!_ In the past I used [skinlf](https://skinlf.dev.java.net/), a Swing framework that allowed me to use GNOME and KDE themes within my application.

Well, going to the root of this post. You can find a real SWT application [here](http://weblogs.javahispano.org/page/mperez/20040317).
<hr />
####
[WoEyE](http://amarok.homeunix.org "woeye@mac.com") - <time datetime="2004-04-05 04:24:54">Apr 1, 2004</time>

Partha: It is possible in OS X to put the menubar of a Swing application where it belongs. You can do this by adding a special system property. I wonder why Netbeans isn't doing this?
<hr />
####
[Partha]( "") - <time datetime="2004-04-05 22:58:40">Apr 1, 2004</time>

Thanks WoEye,
I had to set the following system property to get the menu to correctly show up.
com.apple.macos.useScreenMenuBar=true
<hr />
####
[Jesus M. Rodriguez](http://www.jroller.com/page/jmrodri "jmrodri@nc.rr.com") - <time datetime="2004-04-06 09:46:49">Apr 2, 2004</time>

But if Netbeans were written using SWT, you wouldn't have had to add that property.
<hr />
####
[David Karam](http://www.posttool.com "") - <time datetime="2004-04-18 19:39:03">Apr 0, 2004</time>

SWT seems excellent. How "Java" an API seems is not necessarily my concern. My question is, has anyone found deployment/installation hassles? It even seems easy to do this...
<hr />
####
[Damjan]( "") - <time datetime="2004-05-10 23:50:44">May 1, 2004</time>

SWT vs Swing... The thing I hate about Swing is that it won't use my TTF fonts trough XFT. I write cyrillics a lot, and the fonts Swing supports just don't cut in. On the other hand SWT look great. About the API, I haven't compared the API's of SWT and Swing... but from what I remember I didn't like Swing... so SWT can be no worse :)
<hr />
####
[markus](http://www.outhink.com "markus@outhink.com") - <time datetime="2004-07-07 19:44:55">Jul 3, 2004</time>

We use SWT in our SpinXpress p2p file transfer application. Windows version available now and Macintosh version due out very soon (it takes more than SWT to make software x-platform, but it sure helps). Check it out!
<hr />
