---
title: 'Family tech support'
date: Sun, 25 Nov 2007 18:48:04 +0000
draft: false
tags: [Linux, Technology]
categories: [Linux, Technology]
type: post
---

As a software engineer, I am usually called upon to be the family tech support person. Under most circumstances I am more than willing to do it and actually enjoy it. At home we have weened off of Windows for almost everything except [iTunes](http://www.apple.com/itunes/download/). That's my only weakness as I like how easy it is to buy songs and put them on my [iPod](http://www.apple.com/ipodclassic/).

Friday, I had to fix a printing issue with my [mom's laptop](http://zeusville.wordpress.com/2007/04/08/mom-going-linux/). I tried to help over the phone but it is too difficult to do. The printer would print from the media card but not the computer. Turns out there were almost 30 print jobs stuck in the queue. I removed them all and the printer worked again. Not quite sure what the problem was, but it worked. As I'm writing this I completely forgot to open up the VNC port for remote debugging :( oh well next visit. I forgot to mention my mom's laptop is a Dell 1501 running [Ubuntu](http://www.ubuntu.com/). It has Windows XP Home installed but we don't use it at all. [Ubuntu](http://www.ubuntu.com/) meets all of her computing needs. Also, it's not one of the Dell Ubuntu laptops either, we bought it before that happened.

My father-in-law was having some serious computer issues with his machine, a [Shuttle XPC](http://us.shuttle.com/barebone/BareboneHome.html) with an Athlon XP 2600+, 40GB hard drive, nVidia onboard video and 512 MB RAM. Not a speed machine but still very usable, well it should be considering Liz' PIII 733 with 512MB ram ran just fine until I upgraded it.

So the problem with his machine was, well, it had TOO MUCH SHIT on it. The 40GB drive had about 100MB free. I have no idea how that can get full since he does email, word processing and music. Plus the machine ran slow as molasses. I mean slower than the PIII 733 I mentioned earlier. First thing was to backup his data to a portable [Western Digital 80GB Passport](http://www.wdc.com/en/products/products.asp?driveid=259&language=en). I then removed unused programs. I found 7 versions of Java installed 1.4.1, 1.5.0, 1.6.0 plus updates of each taking up 800MB alone. This was **NOT** his fault, but the way Java updates itself on Windows. This is one place Linux shines.

There were 4 media players: [WINAMP](http://www.winamp.com/), [Windows Media Player](http://www.microsoft.com/windows/windowsmedia/player/10/default.aspx), [Musicmatch](http://www.musicmatch.com/), and [iTunes](http://www.apple.com/itunes/). There was a Spanish version of Microsoft Office 2003 Small Business edition including SQL SERVER! Windows Live OneCare and Mcaffee anti-virus suite, and a bunch of other crap.

What makes me annoyed is not that fact that he asked me to help him with his computer because I like doing it. It's WINDOWS! That's what I really hate. Data files and config files are scattered everywhere. No easy way to get a list of the programs installed or to uninstall them, especially if the uninstaller gets corrupted. Above all Windows is a pain in the @$$ to install as well.

I can re-install a Fedora Linux based machine in a couple hours. I backup /etc, /home, and rpm -qa to get a list of the software. I then install Fedora, setup livna repos, yum install the missing packages I need after a fresh install, then rsync back /home, and any /etc configuration I may need (usually not much). DONE! FINITO! FINIS!

Windows? Um, that's just a hellish process. Install Windows XP with SP1 (part one of the problem). Install drivers for hardware (usually several CDs worth), create users, download software from different places (no repositories like Linux), connect to Windows Update a bazillion times to get all of the proper updates, install other software from CD, copy back data that was backed up and hope we got it all, reconfigure all user settings as that wasn't backed up. Not to mention the bazillion reboots required in the process.

In the process I mention how easy it was to setup Linux and he asked if I could set him up with it. I declined because there are some programs he has that won't run on Linux like [LESSONmaker](http://www.lessonmaker8.com/), [iTunes](http://www.apple.com/itunes/), and many others. I know I should be spreading the Linux word, but I knew there were some problems I couldn't solve easily for him.

This got me thinking, so who is the Linux target market? In my opinion there are two types of users that make great Linux users: 1) folks like my mom who are new to computers 2) power users who understand how computers work and don't mind tinkering. The hardest people to switch to Linux are those that "know enough to be dangerous". Because they buy or use esoteric software off the shelf that have no equivalent solutions in Linux, do lot's of media i.e. music playing, downloaded, etc with their Windows PCs, or don't have the patience to tinker. This is a difficult segment to crack.

After almost 4 hours of dealing with Windows, I gave up and brought the machine to my house to try again without any time pressures. Maybe I'll install [VirtualBox](http://www.virtualbox.org/) or [VMware](http://www.vmware.com/products/) with a Linux image so he can try out Linux to see how it works for him. It would certainly make my life easier to deal with Linux than Windows.

Even with this ordeal I'll still keep helping him with any computer woahs, not just because he's family, but because I still like computers and tinkering.
---
### Comments:
#### [jaxzun14](http://jaxzun14.wordpress.com/ "jacquie.moreno@gmail.com") - <time datetime="2007-11-27 00:31:33">Nov 2, 2007</time>

All I can say is you are a goood sport!!
<hr />
#### [Eric Colon]( "ericcolon@gmail.com") - <time datetime="2007-11-26 21:22:44">Nov 1, 2007</time>

I can't believe Titi is a Linux user...... amazing! :)
<hr />
#### [Máirín Duffy](http://mihmo.livejournal.com/ "mairin@gmail.com") - <time datetime="2007-12-03 14:56:33">Dec 1, 2007</time>

You would be totally amazed by what runs in wine these days. If I try $RANDOM\_WINDOWS\_APPS I have about an 80% success rate of them working in wine. Maybe try some of the apps your father-in-law runs in wine to see if they work well enough for him? We need more converts! :)
<hr />
#### [KristjanS]( "kristjan.siimson@gmail.com") - <time datetime="2007-12-07 15:58:53">Dec 5, 2007</time>

Hint: There is an awesome application similar to iTunes that does work in Linux. If you send me you e-mail to kristjan.siimson@gmail.com, I'll send you an invite back. Why? If you join, I get 50 free songs (if I remember correctly, then so will you).
<hr />
