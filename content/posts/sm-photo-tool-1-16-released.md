---
title: 'sm-photo-tool 1.16 released!'
date: Wed, 05 Aug 2009 04:21:01 +0000
draft: false
tags: [Linux, python, sm-photo-tool]
categories: [Linux, python, sm-photo-tool]
type: post
---

Hey there [Smugmuggers](http://smugmug.com/)! I'm releasing version [1.16](http://github.com/jmrodri/sm-photo-tool/downloads) of [sm-photo-tool](http://github.com/jmrodri/sm-photo-tool/tree/master) tonight. For those that don't know, sm-photo-tool is a command line program that aids in managing your photos on [smugmug.com](http://smugmug.com). Given a directory of photos, you can create a new album on smugmug.com, then upload all of the pictures in the directory into that newly created album.```
\[jmrodri@firebird ~\]$ cd myphotos
\[jmrodri@firebird  myphotos\]$ sm-photo-tool create 'my photos album'
\[my photos album\] created with id \[9164554\]
\[jmrodri@firebird myphotos\]$ sm-photo-tool update
./spaceshuttlehuge.jpg...\[OK\] 939321 bytes 24 seconds 38KB/sec ETA 0
24 939321 bytes 38KB/sec
```This release is mainly a maintenance release but I also refactored the code from a single python file to a series of modules, and cleaned up the available commands. REFACTOR Version [1.15](http://sourceforge.net/projects/sm-photo-tool/files/) of sm-photo-tool contained a single python script, while this is easy to use, it is a bear to maintain. All of the commands were moved into smcommands.py as new classes.  I then replaced all of the horrible option parsing from the previous script in the individual command classes. Thanks to [yum](http://yum.baseurl.org/) and [tito](http://github.com/dgoodwin/tito/tree/master) project for the inspiration in moving the commands to a separate module. COMMAND LINE OPTION CHANGES In the process of refactoring I deemed a few of the commands as redundant and merged them into other commands.```
\[jmrodri@firebird ~\]$ sm-photo-tool 

Usage: sm-photo-tool \[options\] MODULENAME --help

Supported modules:

	create         creates a new gallery and uploads the given files.
	list           Lists the files in an album, or lists available galleries
	upload         Upload the given files to the given gallery\_id.
	full\_update    Mirror an entire directory tree.
	update         Updates gallery with any new or modified images.
```

*   create\_upload no longer exists, it was replaced by create --upload
*   galleries merged with list
*   list gained two new options album and galleries

```
\[jmrodri@firebird ~\]$ sm-photo-tool list --help
Usage: sm-photo-tool list 

Lists the files in an album, or lists available galleries

Options:
  -h, --help           show this help message and exit
  --login=LOGIN        smugmug.com username
  --password=PASSWORD  smugmug.com password
  --quiet              Don't tell us what you are doing
```README If you download the [tarball](http://cloud.github.com/downloads/jmrodri/sm-photo-tool/sm-photo-tool-1.16.tar.gz), do the following:

*   cd /opt/
*   sudo tar -zxf ~/Download/sm-photo-tool-1.16.tar.gz
*   cd sm-photo-tool-1.16/src/
*   copy the smugmugrc to $HOME/.smugmugrc
*   add your login and password to .smugmugrc
*   ./sm-photo-tool --help

Fedora users have an easier time :) <pre>rpm -Uvh http://cloud.github.com/downloads/jmrodri/sm-photo-tool/sm-photo-tool-1.16-2.fc11.noarch.rpm</pre> Happy uploading! If you run into any problems, leave me a comment or write up an issue here: [http://github.com/jmrodri/sm-photo-tool/issues](http://github.com/jmrodri/sm-photo-tool/issues)