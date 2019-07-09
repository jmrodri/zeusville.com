---
title: 'smugmug to flickr rss'
date: Thu, 08 Mar 2007 15:16:28 +0000
draft: false
tags: [sm-photo-tool, Technology]
categories: [sm-photo-tool, Technology]
type: post
---

I like the [flickr](http://www.flickr.com) sidebar [widget](http://blog.donncha.net/flickr-widget/)

which prompted me to upgrade my [flickr](http://www.flickr.com/photos/jmrodri/) account. But I really wanted to use my [smugmug](http://familiarodriguez.smugmug.com) feed as that is my main photo site.

[Wordpress.com](http://www.wordpress.com) offers the flickr widget but nothing for [smugmug](http://www.smugmug.com). I tried the plain RSS sidebar widget but I only get a list of links which isn't quite as cool.

[![smugmug rss feed](/img/2007/03/smugmugrss.png)](/img/2007/03/smugmugrss.png "smugmug rss feed")

I created a perl script that would transform my [smugmug RSS feed](http://familiarodriguez.smugmug.com/hack/feed.mg?Type=nicknameRecentPhotos&Data=familiarodriguez&format=rss200) into a Flickr RSS feed. Smugmug uses a standard RSS 2.0 feed, while flickr uses [Yahoo's media rss](http://search.yahoo.com/mrss). I couldn't find an easy way to do the transformation, so I took the long way of parsing the incoming RSS feed, then creating a new one. I'm running the script on my home server, which runs quite slow at the moment, but it works. :)

![smugmug feed in flickr widget](/img/2007/03/smugmug_in_flickr1.png)

That's pretty cool IMO :) Here is the script, or you can download it from [here](http://sm-photo-tool.svn.sourceforge.net/viewvc/*checkout*/sm-photo-tool/scripts/smugmug_to_flickr_rss.pl):

```


#!/usr/bin/perl

use strict;

use LWP;

use XML::RSS;

my $req = HTTP::Request->new(GET => 'http://familiarodriguez.smugmug.com/hack/feed.mg?Type=nicknameRecentPhotos&Data=familiarodriguez&format=rss200');

my $ua = LWP::UserAgent->new;

my $resp = $ua->request($req);

# rss feed

# my $resp->content;

my $smugrss = new XML::RSS;

$smugrss->parse($resp->content);

my $s2frss = new XML::RSS;

$s2frss->add\_module(prefix=>'media', uri=>'http://search.yahoo.com/mrss/');

# copy the channel

my $smugchan = $smugrss->{'channel'};

$s2frss->channel(title  => $smugchan->{'title'},

                 link   => $smugchan->{'link'},

                 description => $smugchan->{'description'},

                 pubDate => $smugchan->{'pubDate'},

                 lastBuildDate => $smugchan->{'lastBuildDate'},

                 generator => $smugchan->{'generator'},

                 copyright => $smugchan->{'copyright'});

$s2frss->image(title => $smugrss->{'image'}->{'title'},

               url   => $smugrss->{'image'}->{'url'},

               link  => $smugrss->{'image'}->{'link'});

# copy items

foreach my $item (@{$smugrss->{'items'}}) {

   $s2frss->add\_item(

      title       => $item->{'title'},

      link        => $item->{'link'},

      description => $item->{'description'},

      pubDate     => $item->{'pubDate'},

      author      => $item->{'author'},

      guid        => $item->{'guid'},

      category    => $item->{'category'},

      media => {

        title     => $item->{'title'},

        text      => $item->{'description'},

        content => {

          url     => $item->{'enclosure'}->{'url'},

          type    => "image/jpeg",

          height  => "100",  # change later

          width   => "100"

        },

        thumbnail => {

          url     => $item->{'enclosure'}->{'url'},

          height  => "100",  # change later

          width   => "100"

        }

      }

   );

}

print "Content-Type: text/xmlnn";

$s2frss->{output} = "2.0";

print $s2frss->as\_string;


```
---
### Comments:
####
[jmrodri](http://zeusville.wordpress.com/ "jmrodri@gmail.com") - <time datetime="2007-03-08 18:15:54">Mar 4, 2007</time>

It's not perfect yet :) sometimes I lose my feed.
<hr />
####
[P. A.]( "plaajaas@yahoo.com") - <time datetime="2007-11-02 12:24:13">Nov 5, 2007</time>

just wanted to say that i have smugmug and love my flickr sidebar widget on my wordpress blog. i used the smugmug gallery feed (that i found on the Share page) and put it where the api feed thing was for flickr and it works. i just get the most recent pics, but for me that is enough. if my family wants more, they just click on the widget. this might work for other people like me who aren't very technical computer wise. :D
<hr />
####
[Flickr Widget works for SmugMug &laquo; (I am) Strangely Looping](http://strangelylooping.wordpress.com/2009/03/08/flickr-widget-works-for-smugmug/ "") - <time datetime="2009-03-07 23:32:13">Mar 6, 2009</time>

\[...\] WordPress. Tags: SmugMug, WordPress trackback After a bit of searching I ran across a post that described how the author had written a Perl script to convert a SmugMug feed into a Flickr \[...\]
<hr />
