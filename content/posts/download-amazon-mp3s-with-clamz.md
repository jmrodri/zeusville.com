---
title: 'Download Amazon MP3s with clamz'
date: Thu, 13 Jan 2011 15:56:07 +0000
draft: false
tags: [clamz amazon mp3 linux]
categories: [Linux]
type: post
---

While I applaud Amazon for providing an MP3 [downloader](http://www.amazon.com/gp/dmusic/help/amd.html/ref=dm_amd_upgrade_img_1010) for Linux, but it is always several releases behind for Fedora. The current one available is Fedora 11, while the current [Fedora release is 14](http://www.fedora.redhat.com/get-fedora).

For a while there I kept an old Fedora release running in a guest just to download MP3 albums from Amazon, then I found [clamz](http://code.google.com/p/clamz/). It's a command line based amz file downloader. Simple point it to the .amz file and it'll do it's magic:

```
\[jmrodri@firebird Iron Maiden\]$ mkdir "Piece of Mind"

\[jmrodr@firebird Iron Maiden\]$ cd Piece\\ of\\ Mind/

\[jmrodri@firebird Piece of Mind\]$ clamz ~/Download/AmazonMP3-12345...amz 

Downloading "01 - Where Eagles Dare.mp3"

Where Eagles Dare                 \[#################################\]  100% 

Downloading "02 - Revelations (Album Version).mp3"

Revelations (Album Version)       \[#################################\]  100% 

Downloading "03 - Flight Of Icarus (Album Version).mp3"

Flight Of Icarus (Album Version)  \[#################################\]  100% 

Downloading "04 - Die With Your Boots On.mp3"

Die With Your Boots On            \[#################################\]  100% 

Downloading "05 - The Trooper (Album Version).mp3"

The Trooper (Album Version)       \[#################################\]  100% 

Downloading "06 - Still Life.mp3"

Still Life                        \[#################################\]  100% 

Downloading "07 - Quest For Fire.mp3"

Quest For Fire                    \[#################################\]  100% 

Downloading "08 - Sun And Steel.mp3"

Sun And Steel                     \[#################################\]  100% 

Downloading "09 - To Tame A Land.mp3"

To Tame A Land                    \[#################################\]  100% 

1 of 1 AMZ files downloaded successfully.

It's awesome! Checkout [clamz](http://code.google.com/p/clamz/) if you're a Amazon MP3 customer running on Linux.


```