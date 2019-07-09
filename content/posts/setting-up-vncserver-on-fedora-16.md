---
title: 'setting up vncserver on Fedora 16'
date: Fri, 27 Jan 2012 16:42:25 +0000
draft: false
tags: [Linux, Technology]
categories: [Linux, Technology]
type: post
---

Updated to reflect `/etc/systemd`, thanks for all the helpful comments.

* * *

The change to [systemd](http://fedoraproject.org/wiki/Features/systemd) from SysVinit caused a bit of an issue for vncserver configuration. In the past I would edit

```
/etc/sysconfig/vncservers
```, with systemd the process is quite different.

For our example I will setup vncserver to have display :3 running at a resolution of 1600x900. If you want a different number simply replace it with the number of choice.

```


sudo yum install tigervnc-server

sudo cp /lib/systemd/system/vncserver@.service /etc/systemd/system/vncserver@:3.service

Next you will need to edit the service file with the username you want vncserver to run under and any vnc options you want.

```
sudo vi /etc/systemd/system/vncserver@:3.service
```

The file will look something like this when you open it:

```


# comment redacted

\[Unit\]

Description=Remote desktop service (VNC)

After=syslog.target network.target

\[Service\]

Type=forking

ExecStart=/sbin/runuser -l  -c "/usr/bin/vncserver %i"

ExecStop=/sbin/runuser -l  -c "/usr/bin/vncserver -kill %i"

\[Install\]

WantedBy=multi-user.target

Change `<USER>` with the username you want to run vncserver under. For our case let's use `kdr`.

Next add the vnc options you want after the %i. Since we want it to run at a resolution of 1600x900 we will add `-geometry 1600x900`.

```


ExecStart=/sbin/runuser -l kdr -c "/usr/bin/vncserver %i -geometry 1600x900"

ExecStop=/sbin/runuser -l kdr -c "/usr/bin/vncserver -kill %i"

Save the file and enable the service:

```
sudo systemctl enable vncserver@:3.service
```

Now configure the password you want to use to connect to vnc. Run this

as the user you setup in the \*.service file above i.e. kdr.

```
vncpasswd

Password:

Verify:

We now have vncserver setup with a username and a password, and enabled in the system. Two more things to check. First thing is verify you have the port open. The vnc display number will map to 5900 series of ports. Since we chose 3 vncserver will listen on port 5903. If you choose 1, it'll be 5901, etc.

Let's see if iptables is configured to listen to this port:

```
sudo iptables --list | grep 5903

Nope, let's update iptables:

```


sudo vi /etc/sysconfig/iptables

Add this to the file:

```
\-A INPUT -p tcp -m state --state NEW -m tcp --dport 5903 -j ACCEPT
```

Save the file, then restart iptables and verify that the port is active.

```
sudo systemctl restart iptables.service

sudo iptables --list | grep 5903

ACCEPT     tcp  --  anywhere             anywhere             state NEW tcp dpt:5903

Ok FINALLY we can start up vncserver.

```
sudo systemctl start vncserver@:3.service
```

Test it out by connecting with `vncviewer host.example.com:3`.

Enter the password you used for `vncpasswd`.

**ENJOY!**


```
```
```
```
```
```
```
---
### Comments:
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
