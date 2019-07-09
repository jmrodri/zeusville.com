---
title: 'Fedora 13 to Centos 7'
date: Sun, 01 Mar 2015 07:41:04 +0000
draft: false
tags: [centos, fedora, linux, server]
categories: [Linux, python, Technology]
type: post
---

A couple of weeks ago, I finally updated my home server from [Fedora 13](https://lists.fedoraproject.org/pipermail/announce/2011-June/002979.html) to [CentOS 7](http://www.centos.org/). Fedora had the media support but I can't keep the machine updated fast enough. This time I decided to go with another Red Hat derivative so I chose CentOS. The goal is to have an OS that has a longer release cycle. Most of the services I'm running haven't changed in a while (considering Fedora 13 was ancient). This was **NOT** an in place "upgrade". Going to CentOS was a fresh install. I backed up all 70G of the root partition to an external drive then told CentOS to reformat the existing partitions. My biggest worry was the 2TB [RAID 5](http://en.wikipedia.org/wiki/Standard_RAID_levels#RAID_5) array. During the installation I told the installer to mount the array on `/vol` but DO NOT FORMAT. I checked it three times to make sure I didn't lose anything. I did **NOT** backup the RAID array so this was the most dangerous part of the install I did. Once installed the task of restoring the data back to the server, users, configuration, install needed software to support the services I had running on the machine, etc. Because Fedora 13 was so old, I couldn't just `rsync /etc`. First thing I had to do was change the UID and GUID of all the backup files since the default [UID changed](https://lists.fedoraproject.org/pipermail/devel/2011-May/151663.html) from 500 to 1000. I created the users, then I had to change the access to the backed up files and to the [RAID](http://en.wikipedia.org/wiki/RAID) array.```
\# owner
chown -R --from=500 1000 $1
chown -R --from=501 1001 $1
chown -R --from=502 1002 $1
chown -R --from=504 1004 $1
chown -R --from=505 1005 $1
chown -R --from=506 1006 $1
chown -R --from=507 1007 $1

# groups
chown -R --from=:500 :1000 $1
chown -R --from=:501 :1001 $1
chown -R --from=:502 :1002 $1
chown -R --from=:504 :1004 $1
chown -R --from=:505 :1005 $1
chown -R --from=:506 :1006 $1
chown -R --from=:507 :1007 $1

chown -R --from=481:466 992:989 $1

```The firewall switched from [iptables](http://wiki.centos.org/HowTos/Network/IPTables) to [FirewallD](https://fedoraproject.org/wiki/FirewallD). So instead of restoring my `/etc/sysconfig/iptables` file I decided to figure out how to use FirewallD. I wrote a script for each of the iptables ports:```
#...
firewall-cmd --permanent --add-service=http
firewall-cmd --permanent --add-port=PORT#/tcp
#...
firewall-cmd --reload

```Most of the services were easy to get back running: [http](http://httpd.apache.org/), [vnc](http://wiki.centos.org/HowTos/VNC-Server), and [plexmediaserver](https://plex.tv/). Some of the others were a bit tricky to get back up and running. [Streambaby](https://code.google.com/p/streambaby/) had an error with the newer version of [ffmpeg](https://www.ffmpeg.org/). It would fail with:```
Exception in thread "main" java.lang.NoClassDefFoundError: net/sf/ffmpeg\_java/v53/AVFormatLibrary …

```Thankfully, this [post](http://info.vortexbox.org/tiki-index.php?page=InstallStreamBaby) had the suggested solution of simply adding the following to the `streambaby.ini````
com.unwiredappeal.tivo.vm.ffjava.FFmpegJavaVideoModule=false
ffmpegexe.transcode.sameqargs=-ab 192k

```Other Streambaby & multimedia resources: [https://code.google.com/p/streambaby/wiki/StreamBabyIni](https://code.google.com/p/streambaby/wiki/StreamBabyIni) [http://info.vortexbox.org/tiki-index.php?page=InstallStreamBaby](http://info.vortexbox.org/tiki-index.php?page=InstallStreamBaby) [http://wiki.centos.org/TipsAndTricks/MultimediaOnCentOS7](http://wiki.centos.org/TipsAndTricks/MultimediaOnCentOS7) Next up was to revive the [NFS](http://www.unixmen.com/setting-nfs-server-client-centos-7) shares.

*   copy over `/etc/exports`
*   remember firewall settings are the most important part
*   remove `nfsver-3` from the fstab on the client side
*   refresher blog: [http://www.unixmen.com/setting-nfs-server-client-centos-7](http://www.unixmen.com/setting-nfs-server-client-centos-7)

The server also acts as a [TimeMachine](http://en.wikipedia.org/wiki/Time_Machine_%28OS_X%29) drive to backup our MacBook Pro. The old server used netatalk 2.x so the configuration files changed here too.

*   config files moved from `/etc/atalk` to `/etc/netatalk`
*   afpd.conf became afp.conf
*   afp conf is completely different

I basically followed the following sources: [http://netatalk.sourceforge.net/wiki/index.php/Netatalk\_3.1.7\_SRPM\_for\_Fedora\_and\_CentOS](http://netatalk.sourceforge.net/wiki/index.php/Netatalk_3.1.7_SRPM_for_Fedora_and_CentOS) [http://netatalk.sourceforge.net/3.1/htmldocs/configuration.html#idp139639181431264](http://netatalk.sourceforge.net/3.1/htmldocs/configuration.html#idp139639181431264) The last service was to setup [VirtualBox](https://www.virtualbox.org/) to run headless for my [Windows 7](http://en.wikipedia.org/wiki/Windows_7) guest. See [VirtualBox installation](http://wiki.centos.org/HowTos/Virtualization/VirtualBox) it wasn't that difficult. That's was pretty much the only things I hit during the "upgrade". It took a couple days to get everything up and running. I did it one service at a time. One lesson I learned? Don't wait so long to update your servers :)