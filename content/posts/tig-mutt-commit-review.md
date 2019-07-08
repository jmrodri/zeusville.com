---
title: 'tig + mutt = commit review'
date: Tue, 30 Mar 2010 17:31:37 +0000
draft: false
tags: [Linux, sm-photo-tool, Technology]
type: post
---

I spend some of my time reviewing team members commits. Typically I'd use the RSS feed from Google Reader, but it doesn't have the actual diff to comment on. [![](http://zeusville.files.wordpress.com/2010/03/greader-review1.png "git rss feed in Google Reader")](http://zeusville.files.wordpress.com/2010/03/greader-review1.png) Most of the time I use [tig](https://git.wiki.kernel.org/index.php/Tig) to view the commits. And instinctively I'd want to email the author with my comments, so here's how to do that. I'm sure there are easier commands but this is what worked for me, your experience may vary. [![](http://zeusville.files.wordpress.com/2010/03/tig-main.png "tig-main")](http://zeusville.files.wordpress.com/2010/03/tig-main.png) First thing I did was create a [git alias](https://git.wiki.kernel.org/index.php/Aliases) which is useful by itself. It outputs the commit to a temp file, then gets the title and the author's email address from the same commit passing that to [mutt](http://www.mutt.org/).```
\[alias\]
    ...
    prepmail = !sh -c 'git show $1 > /tmp/commit && mutt -s \\"\`git show --pretty=format:\\"%s\\" $1 | head -n 1\`\\" -i /tmp/commit -- \\"\`git show --pretty=format:\\"%ae\\" $1 | head -n 1\`\\"' -

```Now I want to be able to press a key in [tig](https://git.wiki.kernel.org/index.php/Tig) at the diff screen to reply to the author's commit. Simply [bind a key](http://jonas.nitro.dk/tig/tigrc.5.html), in my case I bound s in the diff view to call git prepmail with the commit's SHA1. In your $HOME/.[tigrc](http://jonas.nitro.dk/tig/tigrc.5.html) add the following line. Checkout the [tigrc man page](http://jonas.nitro.dk/tig/tigrc.5.html) for more information.```
bind diff s !git prepmail %(commit)

```Now in the diff view press 's' and tig will launch mutt with the appropriate information. [![](http://zeusville.files.wordpress.com/2010/03/tig-default2.png "tig-default")](http://zeusville.files.wordpress.com/2010/03/tig-default2.png) The email shows up first: [![](http://zeusville.files.wordpress.com/2010/03/tig-email.png "tig-email")](http://zeusville.files.wordpress.com/2010/03/tig-email.png) Followed by the email's subject, notice it matches the commit's message. [![](http://zeusville.files.wordpress.com/2010/03/tig-subject.png "tig-subject")](http://zeusville.files.wordpress.com/2010/03/tig-subject.png) And finally, the diff as an email body allowing you to comment on the changes to the author. [![](http://zeusville.files.wordpress.com/2010/03/tig-body.png "tig-body")](http://zeusville.files.wordpress.com/2010/03/tig-body.png) So a simple git alias in $HOME/.gitconfig, a key binding for $HOME/.tigrc, and you can now review commits using [tig](https://git.wiki.kernel.org/index.php/Tig). Enjoy!