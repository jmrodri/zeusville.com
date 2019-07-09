---
title: 'Apply github pull requests as patches'
date: Fri, 01 Feb 2013 16:35:19 +0000
draft: false
tags: [Linux, Technology]
categories: [Linux, Technology]
type: post
---

[Our team](https://github.com/candlepin/) uses Github's [pull requests](https://help.github.com/articles/using-pull-requests) as a code review process, which requires a fair number of requests that need to be tested. Github has a [really cool feature](https://help.github.com/articles/using-pull-requests#merging-a-pull-request) where if you put the `.patch` extension to the url it will show you a diff that can be passed to `git am`.

So given a pull request 162 ([https://github.com/candlepin/candlepin/pull/162](https://github.com/candlepin/candlepin/pull/162)) you can use `curl` to download the patch and then pipe it to `git am`. Once you're done reviewing, simply revert your branch back using `git reset --hard origin/master`.

I added some functions to my `.bashrc` for the projects I review most often, here's the snippet:

```


# apply the given pull request from the given project as a patch

# arg: project (i.e. candlepin/subscription-manager/etc

# arg: pull request number

\_\_github ()

{

    curl https://github.com/candlepin/$1/pull/$2.patch | git am

}

# apply the given pull request for candlepin

# arg: pull request number

cppull ()

{

    \_\_github "candlepin" $1

}

# apply the given pull request for subscription-manager

# arg: pull request number

submanpull ()

{

    \_\_github "subscription-manager" $1

}

### Summary

*   `curl https://github.com/candlepin/candlepin/162.patch | git am`

*   TEST PATCH

*   `git reset --hard origin/master`




```
---
### Comments:
####
[ringmaster](http://asymptomatic.net/ "a_wordpress@midnightcircus.com") - <time datetime="2013-02-01 14:35:21">Feb 5, 2013</time>

You can do a similar thing with git aliases, which allow you to run shell commands using what looks like a git command, like \`git cppull 4\`: http://stackoverflow.com/questions/1309430/how-to-embed-bash-script-directly-inside-a-git-alias There are a ton of really slick aliases available that can change the way you work with git: https://git.wiki.kernel.org/index.php/Aliases
<hr />
####
[lzap](http://gravatar.com/lzap "lzap@seznam.cz") - <time datetime="2013-02-03 18:06:33">Feb 0, 2013</time>

Definitely interesting and I have been doing this for a while, but why not to do what github.com says in the mail :) git checkout -b temp git pull https://github.com/parthaa/katello runcible-0.3.2-changes # review time! git branch -D temp Advantage of this is you can stop your review and get back to it easily later.
<hr />
