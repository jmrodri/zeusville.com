---
title: 'Fedora 8 ROCKS!'
date: Thu, 08 Nov 2007 14:44:51 +0000
draft: false
tags: [Linux]
categories: [Linux]
type: post
---

I installed Fedora 8 RC on Monday night. I chose to backup my homedir and do a fresh install of Fedora 8 instead of upgrading my Fedora Core 6 install. I went this route mostly because my Fedora Core 6 was an upgrade of Fedora Core 5 which was an upgrade of Fedora Core 5 Test 1,2,3 :) Figured it was time to get out any cruft that may have been lying around.

The install went fairly well. I chose virtualization during install, then chose not to install Xen. But something I clicked on caused Xen to get installed anyway making it the default kernel at first boot. A quick edit of grub.conf fixed that.

I then rsync'd my homedir back over and logged in. Some of the applets didn't start because I had forgotten to install them. Not a big deal,that was my fault not Fedora's.

The only real problem I ran into was trying to turn on "Desktop Effects", with my copied over homedir, the window borders wouldn't show up when Desktop Effects was enabled. But if I logged in as another user with freshly generated configs it worked. So I threw away my configs and recreated my homedir and logged in to have GNOME create the basic entries, VIOLA! Desktop Effects worked (for about 40 minutes then a hard lockup of X) :( I should've figured as much as my previous attempts resulted in the same behavior: [try #1](http://zeusville.wordpress.com/2007/03/06/desktop-effects-locks-up-my-box/) and [try #2](http://zeusville.wordpress.com/2007/03/07/desktop-effects-locks-up-my-box-part-2/).

Another little problem is with [NetworkManager](http://www.gnome.org/projects/NetworkManager/) 0.7 and static ips. In FC6, [NetworkManager](http://www.gnome.org/projects/NetworkManager/) worked GREAT with my static ip. But the one in Fedora 8 INSISTS on doing a dhcp request. I know I can do with out [NetworkManager](http://www.gnome.org/projects/NetworkManager/) as I'm not using wireless, but I'm fond of the vpnc menu in [NetworkManager.](http://www.gnome.org/projects/NetworkManager/)

So far no show stopper problems. Fedora 8 has beautiful [artwork](http://fedoraproject.org/wiki/Artwork/F8Themes), a cool new [GNOME vnc client](http://www.gnome.org/projects/vinagre/), and [online desktop](http://fedoraproject.org/wiki/Releases/FeatureOnlineDesktop).

Fedora is like a fine wine, it gets better with age.

Kudos to the Fedora members for a fine release.
---
### Comments:
#### [Traces of Martin's State](http://eightflat.org/tracesofmartinsstate/2007/11/10/quick-test-of-the-fedora-8-kde-livecd/ "") - <time datetime="2007-11-10 13:18:34">Nov 6, 2007</time>

**Quick test of the Fedora 8 KDE LiveCD** Hi all, here is a small “report” on my findings after having tried Fedora 8 KDE LiveCD for half an hour on my Dell Latitude X1. See my previous notes on earlier Fedora versions here. Please note that the KDE LiveCD is not exactly the same a...
<hr />
