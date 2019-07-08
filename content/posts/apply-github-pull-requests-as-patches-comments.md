---
title: 'Apply github pull requests as patches'
date: Fri, 01 Feb 2013 16:35:19 +0000
draft: false
tags: [Linux, Technology]
---


#### 
[ringmaster](http://asymptomatic.net/ "a_wordpress@midnightcircus.com") - <time datetime="2013-02-01 14:35:21">Feb 5, 2013</time>

You can do a similar thing with git aliases, which allow you to run shell commands using what looks like a git command, like \`git cppull 4\`: http://stackoverflow.com/questions/1309430/how-to-embed-bash-script-directly-inside-a-git-alias There are a ton of really slick aliases available that can change the way you work with git: https://git.wiki.kernel.org/index.php/Aliases
<hr />
#### 
[lzap](http://gravatar.com/lzap "lzap@seznam.cz") - <time datetime="2013-02-03 18:06:33">Feb 0, 2013</time>

Definitely interesting and I have been doing this for a while, but why not to do what github.com says in the mail :) git checkout -b temp git pull https://github.com/parthaa/katello runcible-0.3.2-changes # review time! git branch -D temp Advantage of this is you can stop your review and get back to it easily later.
<hr />
