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