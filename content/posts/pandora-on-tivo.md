---
title: 'Pandora on TiVo'
date: Thu, 05 Aug 2010 02:20:17 +0000
draft: false
tags: [gstreamer, linux, pandora, pianobar, pytivo, tivo]
categories: [Linux]
type: post
---

I'm an avid [Pandora](http://www.pandora.com/) listener and upgraded to [Pandora One](http://www.pandora.com/pandora_one). I'm also a [TiVo](http://www.tivo.com) owner as well. I was a little disappointed when I found out Pandora isn't [available](http://pr.tivo.com/easyir/customrel.do?easyirid=CA934452BA6418EF&version=live&prid=599424&releasejsp=custom_150#morecontent) on TiVo yet.

I have a server running [pyTivo](http://pytivo.sourceforge.net/wiki/index.php/PyTivo) to stream my music and photos to my TiVo. I wanted to listen to my Pandora account on my TiVo and not wait for TiVo to do it. My plan is to use the [TiVo HME SDK](http://tivohme.sourceforge.net/) to write my own app, but in the short term I did the poor mans version.

My server is headless, so I'm running a command-line Pandora client called [pianobar](http://github.com/PromyLOPh/pianobar). While it plays the audio, I wanted to know how to stream it via HTTP instead of the speakers. I found that you can use [gstreamer](http://www.gstreamer.net/) to tap into the [pulseaudio](http://fedoraproject.org/wiki/Releases/FeaturePulseaudio) monitor. WIth [gstreamer](http://www.gstreamer.net/) I can take the [PCM](http://en.wikipedia.org/wiki/Pulse-code_modulation) audio, convert it to mp3 and send it to the [icecast](http://www.icecast.org/) server.

In order to do this, you need to find out the pulseaudio monitor device. I typically run:

```
pactl list > /tmp/output
```Then I look for the Sink with a **State:** of **RUNNING**. Then grab the **Monitor Source:**. Once you have the monitor source, you can use gstreamer to do the rest.

```
gst-launch pulsesrc device=MONITORSOURCEVALUE ! audioconvert ! lame name=enc mode=0 vbr-quality=6 ! shout2send mount=/pandora.mp3 port=8000 password=hackme ip=192.168.1.10
```

Last step is to create an [.m3u](http://hanna.pyxidis.org/tech/m3u.html) file to put in your music folder configured in pyTivo. Mine is simply one line:

```
http://192.168.1.10:8000/pandora.mp3
```

Now in your [TiVo](http://www.tivo.com) menu, select "Music & Photos", select MyMusic (or what ever you called your music share in pyTivo). Find the .m3u file, and select the url that's inside. Sit back and listen to your [Pandora](http://www.pandora.com) stream on your TiVo.
---
### Comments:
#### [Tammy Raines]( "tammyraines38@gmail.com") - <time datetime="2013-12-13 21:12:44">Dec 5, 2013</time>

I have pandora one an can't get it to play on my tiva plz help
<hr />
