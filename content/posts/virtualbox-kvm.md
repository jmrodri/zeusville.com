---
title: 'VirtualBox -> KVM'
date: Wed, 13 Oct 2010 21:24:38 +0000
draft: false
tags: [Linux]
categories: [Linux]
type: post
---

I made the switch today to move from [VirtualBox](http://www.virtualbox.org/) to [KVM](http://www.linux-kvm.org/page/Main_Page) on my Fedora 13 workstation. At first I thought I would have to reinstall all of my guests, then I found this blog on how to convert VirtualBox guests to work in KVM: [Convert Virtualbox vid to KVM qcow](http://blog.bodhizazen.net/linux/convert-virtualbox-vdi-to-kvm-qcow/).

I left them as raw images (not sure if that's good or bad, but it works) :)

First, convert your VirtualBox [vdi](http://en.wikipedia.org/wiki/Virtual_disk_image) files to raw format:

```
VBoxManage clonehd --format RAW fedora13.vdi fedora13.img
```

Notice I did **NOT** pass in the path to the vdi file. VBoxManage will magically know where to find it.

Then I moved the `.img` file to `/var/lib/libvirt/images`:

```
sudo mv .VirtualBox/HardDisks/fedora13.img /var/lib/libvirt/images/
```

Once I had the images copied, I started `virt-manager` to create my guests. Click the _New_ button and follow along in the wizard.

[![](/img/2010/10/virtmgr1.png "Virt-manager")](/img/2010/10/virtmgr1.png)

First give your VM a name, and select _Import existing disk image_, press _Forward_.

[![](/img/2010/10/virtmgr2.png "New VM step 1")](/img/2010/10/virtmgr2.png)

Next, set the _OS type_ and _Version_ (not sure if this is required). Enter the path to the image or use the _Browse_ button.

[![](/img/2010/10/virtmgr3.png "New VM step 2")](/img/2010/10/virtmgr3.png)

Find the image in the list, select it, press _Choose Volume_.

[![](/img/2010/10/virtmgr4.png "Locate storage")](/img/2010/10/virtmgr4.png)

Now you have a storage configured, click _Forward_ to finish creating your guest.

[![](/img/2010/10/virtmgr5.png "New VM (selected image)")](/img/2010/10/virtmgr5.png)

Set the desired _Memory (RAM)_ and _CPUs_, followed by clicking _Forward_ button.

[![](/img/2010/10/virtmgr6.png "New VM (step 3)")](/img/2010/10/virtmgr6.png)

Click _Finish_ to add it to the list of guests.

[![](/img/2010/10/virtmgr7.png "New VM step 4")](/img/2010/10/virtmgr7.png)

Select the guest from the list, press _Run_ button, and watch it start.

[![](/img/2010/10/virtmgr8.png "VM created")](/img/2010/10/virtmgr8.png)

There you go a running KVM guest that started life as a VirtualBox guest.

[![](/img/2010/10/virtmgr9.png "Fedora 13 up and running in KVM")](/img/2010/10/virtmgr9.png)
---
### Comments:
#### [bodhi.zazen](http://bodhizazen.net "bodhizazen@ubuntu.com") - <time datetime="2010-10-13 22:10:15">Oct 3, 2010</time>

Thank you for linking to my blog, glad it helped you.
<hr />
#### [bodhi.zazen](http://bodhizazen.net "bodhizazen@ubuntu.com") - <time datetime="2010-11-08 19:13:44">Nov 1, 2010</time>

If you do not mind, here is how to bridge your network card: http://blog.bodhizazen.net/linux/virt-manager-bridged-networking/ I also have a blog on how to "bridge" wireless cards (search my blog if interested, one link is enough here). In terms of KVM vs VBox - It depends on what you want to do exactly. VBox- better for desktops and desktop integration (if you want those things). KVM- better for servers (IMO).
<hr />
#### [Andy]( "andy@st-chads.freeserve.co.uk") - <time datetime="2010-10-14 08:52:25">Oct 4, 2010</time>

Can I ask why you moved? Also, if you used the same host, can you tell us about relative performance kvm vs virtualbox? -Andy
<hr />
#### [Matt](http://bonecho.wordpress.com/ "matthewgwilkinson@gmail.com") - <time datetime="2010-10-14 10:07:10">Oct 4, 2010</time>

Yeah I would be interested in how VirtualBox stacks up against KVM on Fedora. I am thinking about doing the same, but VirtualBox seems like it has many features and a much more polished GUI, settings, etc. etc.
<hr />
#### [David]( "kg4giy@gmail.com") - <time datetime="2010-10-14 11:16:06">Oct 4, 2010</time>

Does this work with that "other" operating system too? I had serious problems installing XP under KVM, so I have to use BOTH on my system and I would like to dump Virtual Box if I can.
<hr />
#### [David]( "kg4giy@gmail.com") - <time datetime="2010-10-14 12:09:27">Oct 4, 2010</time>

The short answer is no, BSOD.
<hr />
#### [Matt](http://bonecho.wordpress.com/ "matthewgwilkinson@gmail.com") - <time datetime="2010-10-14 13:12:11">Oct 4, 2010</time>

Everything worked for me as you've laid out here, however the deal-breaker came when I realized there was no immediate option to use bridged networking. I use Windows XP as a VM under VirtualBox so that I can use software like VMware vSphere Client and MS Outlook. I can't connect to my domain if I can't use the same subnet as eth0...
<hr />
#### [Matt](http://bonecho.wordpress.com/ "matthewgwilkinson@gmail.com") - <time datetime="2010-10-14 13:20:49">Oct 4, 2010</time>

This might work though... http://www.howtoforge.com/virtualization-with-kvm-on-a-fedora-11-server :)
<hr />
