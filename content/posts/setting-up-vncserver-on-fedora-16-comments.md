---
title: 'setting up vncserver on Fedora 16'
date: Fri, 27 Jan 2012 16:42:25 +0000
draft: false
tags: [Linux, Technology]
---


#### 
[Tomasz](http://zdzichu.soup.io "tomek@pipebreaker.pl") - <time datetime="2012-01-27 17:50:35">Jan 5, 2012</time>

Also, when copying files target should be /etc/systemd/system; /lib is for package manager, /etc is for admin.
<hr />
#### 
[mether]( "rahulsundaram@gmail.com") - <time datetime="2012-01-27 15:24:45">Jan 5, 2012</time>

You need to read http://fedoraproject.org/wiki/Systemd#How\_do\_I\_customize\_a\_unit\_file.2F\_add\_a\_custom\_unit\_file.3F It is much more simpler than what you are doing
<hr />
#### 
[ssh DISPLAY issues and remote DESKTOP](http://www.linuxquestions.org/questions/linux-networking-3/ssh-display-issues-and-remote-desktop-4175434262/#post4815788 "") - <time datetime="2012-10-26 17:39:46">Oct 5, 2012</time>

\[...\] is wrong with this? besides, I want to configure remote desktop TigerVNC following the guide: http://zeusville.wordpress.com/2012/...-on-fedora-16/ the author said: \[...\]
<hr />
#### 
[Charles Brown]( "browx24@yahoo.com") - <time datetime="2012-11-02 08:57:54">Nov 5, 2012</time>

I agree with Miguel. The root cause of these timeout problems is port status being open/close or fire wall. You must have a strong background on iptables maintenance. Meaning you'll be making updates in the iptables. What goes into the iptables and follows after an iptables updates.
<hr />
#### 
[jmrodri](http://zeusville.wordpress.com/ "jmrodri@gmail.com") - <time datetime="2012-04-02 14:59:06">Apr 1, 2012</time>

Miguel, If you are getting a connection timeout I'd double check your port numbers and iptables. Make sure that which ever number you are using for your vncserver matches 590x port number. For example, if you choose 1 port = 5901, 2 then 5902. Also, don't use 0 because that's the remote-desktop vino-server listening on 5900.
<hr />
#### 
[miguel]( "miguel.de.sousa@gmail.com") - <time datetime="2012-04-02 14:14:40">Apr 1, 2012</time>

Hi there, your tut its easy to follow and i think i did every thing right but,... i get a connection timeout any idea what i might have done wrong? or didnt do?
<hr />
#### 
[SUNG HUN IM]( "ish05041@gmail.com") - <time datetime="2013-10-08 15:05:23">Oct 2, 2013</time>

I Can't "sudo systemctl enable vncserver@:3.service" Because, Fedora19 say " Failed to issue method call: File exists."
<hr />
#### 
[Imran Khan](http://linuxrnd.blogspot.in "linuxrndblog@gmail.com") - <time datetime="2013-01-30 11:45:26">Jan 3, 2013</time>

Setup VNC Server on Fedora 17 as per above instruction but I'm not getting ping response of VPS.
<hr />
#### 
[Satheesh]( "satheesh.kris@gmail.com") - <time datetime="2013-01-31 20:23:50">Jan 4, 2013</time>

I am able to get around "getpassword error: Inappropriate ioctl for device" problem by installing tigervnc (yum install vnc)
<hr />
#### 
[Emile]( "emile@jcwmail.co.za") - <time datetime="2012-05-07 10:07:00">May 1, 2012</time>

Hi there. I have installed a fresh copy of fedora 16 64bit. I follow all the above steps but when i type 'sudo systemctl start vncserver@:3.service' i get this error. 'Job failed. See system logs and 'systemctl status' for details.' And in /var/log/messages i see the following. 'May 7 15:50:34 Simba runuser\[1625\]: You will require a password to access your desktops. May 7 15:50:34 Simba runuser\[1625\]: getpassword error: Inappropriate ioctl for device May 7 15:50:34 Simba systemd\[1\]: vncserver@:3.service: control process exited, code=exited status=1 May 7 15:50:34 Simba systemd\[1\]: Unit vncserver@:3.service entered failed state.' Also tried running yum update before installing vncserver but stil no luck.
<hr />
