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

[![smugmug rss feed](http://zeusville.files.wordpress.com/2007/03/smugmugrss.png)](http://zeusville.files.wordpress.com/2007/03/smugmugrss.png "smugmug rss feed")

I created a perl script that would transform my [smugmug RSS feed](http://familiarodriguez.smugmug.com/hack/feed.mg?Type=nicknameRecentPhotos&Data=familiarodriguez&format=rss200) into a Flickr RSS feed. Smugmug uses a standard RSS 2.0 feed, while flickr uses [Yahoo's media rss](http://search.yahoo.com/mrss). I couldn't find an easy way to do the transformation, so I took the long way of parsing the incoming RSS feed, then creating a new one. I'm running the script on my home server, which runs quite slow at the moment, but it works. :)

![smugmug feed in flickr widget](http://zeusville.files.wordpress.com/2007/03/smugmug_in_flickr1.png)

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