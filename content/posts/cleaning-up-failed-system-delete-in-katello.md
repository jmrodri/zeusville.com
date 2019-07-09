---
title: 'Cleaning up failed system delete in Katello'
date: Wed, 18 Jul 2012 18:00:35 +0000
draft: false
tags: [Linux, Technology]
categories: [Linux, Technology]
type: post
---

Some how I got my CloudForms SystemEngine into a weird state. I unregistered a consumer while simultaneously removing it from the Katello UI. This caused a race condition because the UI got a 410 GONE error from Candlepin and it didn't remove it from its database. Clearly a bug but still that left me in a state where the Systems page would show the 410 ERROR and leave me with a spinning cursor.

[![](/img/2012/07/410error.png "410error")](/img/2012/07/410error.png)

[![](/img/2012/07/spinningcursor.png "spinningcursor")](/img/2012/07/spinningcursor.png)

As this was simply a test setup I could've just reinstalled. But I wanted to know how this works. As you know Katello is made of many parts: [Pulp](http://pulpproject.org/), [Candlepin](http://candlepinproject.org/), and [Foreman](http://theforeman.org/).

![](http://katello.org/images/arch-diagram.png "katello diagram")

My particular installation didn't have Foreman, so that left: Pulp, Candlepin, Katello proper, and Elasticsearch. Since we were getting a 410 from Candlepin that means the consumer was already gone from that database

```
cp\_consumer
```table.

First, I removed the system from Katello's database.

```


# psql -U katellouser katelloschema

katelloschema=> delete from systems where id = 1;

katelloschema=> commit;

katelloschema=> \\q

Then I removed the consumer from Pulp:

```


# mongo

MongoDB shell version: 1.8.2

connecting to: test

> show dbs

admin	(empty)

local	(empty)

pulp\_database	0.203125GB

> use pulp\_database

switched to db pulp\_database

> show collections

...

consumers

...

> db.consumers.remove()

>

What in the world did you just do? :) We can see that pulp uses the

```
pulp\_database
```. And that one of the collections was ```
consumers
```. Running ```
db.consumers.help()
``` revealed there was a remove method. In my case I only had one system so I just did ```
db.consumers.remove()
```. But if you have more you'll want to specify the key: ```
db.consumers.remove({"\_id":"62d61426-3cf9-4afb-bc3b-e0f696950adc"})
```. Ok we're done. Let's go checkout Katello again.

**UGH** Still shows spinning cursor. So what else could be pointing to the fact that we had a system? Elasticsearch which is the search engine for Katello. That just needs reindexing.

```


# cd /usr/share/katello

# rake reindex

Search Indices cleared.

Re-indexing ActivationKey

Re-indexing Changeset

Re-indexing Filter

Re-indexing GpgKey

Re-indexing Notice

Re-indexing Organization

Re-indexing Provider

Re-indexing Role

Re-indexing SyncPlan

Re-indexing System

Re-indexing TaskStatus

Re-indexing User

Re-indexing Repositories

#

Ok let's try one more time. Visit your systems page in Katello and now you should see that there is no longer a spinning cursor, but a blank list of systems. This is what I expected. **YAY!**

[![](/img/2012/07/cleared.png "cleared")](/img/2012/07/cleared.png)


```
```
```
---
### Comments:
####
[jmrodri](http://zeusville.wordpress.com/ "jmrodri@gmail.com") - <time datetime="2012-07-26 12:48:47">Jul 4, 2012</time>

Removed the extra 'rake' in the 'rake reindex' statement.
<hr />
####
[Marcus]( "marcus.moeller@ubuntu.com") - <time datetime="2012-07-18 14:48:51">Jul 3, 2012</time>

Thanks for pointing that out. I guess you also reported a bug on that ;)
<hr />
####
[jmrodri](http://zeusville.wordpress.com/ "jmrodri@gmail.com") - <time datetime="2012-07-18 15:11:36">Jul 3, 2012</time>

Marcus, yes I did: https://bugzilla.redhat.com/show\_bug.cgi?id=841317
<hr />
####
[Garik Khachikyan](http://gravatar.com/gkhachik "gkhachikyan@gmail.com") - <time datetime="2012-07-19 03:09:49">Jul 4, 2012</time>

Something similar I have reported too: https://bugzilla.redhat.com/show\_bug.cgi?id=841244
<hr />
