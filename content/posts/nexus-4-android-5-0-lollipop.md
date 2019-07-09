---
title: 'Nexus 4 Android 5.0 Lollipop'
date: Mon, 24 Nov 2014 04:21:37 +0000
draft: false
tags: [Personal]
categories: [Personal]
type: post
---

For some reason the Lollipop OTA wouldn't install on my Nexus 4. It kept failing with the following error:

```


Package expects build fingerprint of

google/occam/mako:4.4.4/KTU84P/1227136:user/release-keys or

google/occam/mako:5.0/LRX21T/1576899:user/release-keys: this device has

google/occam/mako:4.4.2/KOT49H/937116:user/release-keys.

E:Error in

/cache/1c6f10c34ed54fb29844906b2f041c900ba23a6b.signed-occam-LRX21T-from-KTU84P.1c6f10c3.zip

I tried a couple of times but no avail. The reports I read mentioned something might have changed for being root. I unlocked and rooted the Nexus 4 when I bought it, but I don't remember really doing anything that really should've messed anything up. But oh well. I even tried flashing the two recoveries that matched: KOT49H and KTU84P. That didn't help.

So I downloaded the factory image and ran the flash-all.sh.

```


\[jesusr@dhcp137-228 occam-lrx21t\]$ adb reboot bootloader

\[jesusr@dhcp137-228 occam-lrx21t\]$ ./flash-all.sh 

sending 'bootloader' (2264 KB)...

OKAY \[  0.073s\]

writing 'bootloader'...

OKAY \[  0.370s\]

finished. total time: 0.443s

rebooting into bootloader...

OKAY \[  0.001s\]

finished. total time: 0.001s

sending 'radio' (45537 KB)...

OKAY \[  1.437s\]

writing 'radio'...

OKAY \[  3.373s\]

finished. total time: 4.811s

rebooting into bootloader...

OKAY \[  0.001s\]

finished. total time: 0.001s

archive does not contain 'boot.sig'

archive does not contain 'recovery.sig'

archive does not contain 'system.sig'

--------------------------------------------

Bootloader Version...: MAKOZ30f

Baseband Version.....: XXXXXX-XXXXXXXX-2.0.1701.04

Serial Number........: XXXXXXXXXXXXXXXX

--------------------------------------------

checking product...

OKAY \[  0.002s\]

checking version-bootloader...

OKAY \[  0.002s\]

checking version-baseband...

OKAY \[  0.002s\]

sending 'boot' (6348 KB)...

OKAY \[  0.204s\]

writing 'boot'...

OKAY \[  0.397s\]

sending 'recovery' (6892 KB)...

OKAY \[  0.220s\]

writing 'recovery'...

OKAY \[  0.398s\]

erasing 'system'...

OKAY \[  3.935s\]

sending 'system' (809641 KB)...

OKAY \[ 25.481s\]

writing 'system'...

OKAY \[ 62.844s\]

erasing 'userdata'...

OKAY \[ 76.469s\]

formatting 'userdata' partition...

Creating filesystem with parameters:

    Size: 14129561600

    Block size: 4096

    Blocks per group: 32768

    Inodes per group: 8144

    Inode size: 256

    Journal blocks: 32768

    Label: 

    Blocks: 3449600

    Block groups: 106

    Reserved block group size: 847

Created filesystem with 11/863264 inodes and 95427/3449600 blocks

sending 'userdata' (137438 KB)...

writing 'userdata'...

OKAY \[ 13.446s\]

erasing 'cache'...

OKAY \[  0.190s\]

formatting 'cache' partition...

Creating filesystem with parameters:

    Size: 587202560

    Block size: 4096

    Blocks per group: 32768

    Inodes per group: 7168

    Inode size: 256

    Journal blocks: 2240

    Label: 

    Blocks: 143360

    Block groups: 5

    Reserved block group size: 39

Created filesystem with 11/35840 inodes and 4616/143360 blocks

sending 'cache' (10984 KB)...

writing 'cache'...

OKAY \[  1.029s\]

rebooting...

finished. total time: 184.628s

\[jesusr@dhcp137-228 occam-lrx21t\]$ 

Phone has rebooted and re-downloading apps from Google. Next I'll restore my Helium backup hopefully that worked :)


```
```