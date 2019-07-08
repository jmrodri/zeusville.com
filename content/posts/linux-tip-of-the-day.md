---
title: 'Linux Tip of the Day'
date: Tue, 11 May 2004 10:54:43 +0000
draft: false
tags: [Linux]
type: post
---

I use df a lot but found it's output useless. And I never thought of figuring out how to change it. So I decided to RTFM (man df). And viola! there's the "human readable" format.

df gives you:

```
\]$ df
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/hda3             36235016   4115460  30278912  12% /
/dev/hda1               202220     25127    166653  14% /boot
/dev/hdb1             38448276   4447508  32047668  13% /home
none                    514016         0    514016   0% /dev/shm

```df -Th gives you:

```
\]$ df
Filesystem    Type    Size  Used Avail Use% Mounted on
/dev/hda3     ext3     35G  4.0G   29G  12% /
/dev/hda1     ext3    198M   25M  163M  14% /boot
/dev/hdb1     ext3     37G  4.3G   31G  13% /home
none         tmpfs    502M     0  502M   0% /dev/shm

```  
I aliased df to df -Th in my .bashrc (alias df='df -Th'). Now when I type df, I get the nice output.