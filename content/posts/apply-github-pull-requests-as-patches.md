---
title: 'Apply github pull requests as patches'
date: Fri, 01 Feb 2013 16:35:19 +0000
draft: false
tags: [Linux, Technology]
type: post
---

[Our team](https://github.com/candlepin/) uses Github's [pull requests](https://help.github.com/articles/using-pull-requests) as a code review process, which requires a fair number of requests that need to be tested. Github has a [really cool feature](https://help.github.com/articles/using-pull-requests#merging-a-pull-request) where if you put the `.patch` extension to the url it will show you a diff that can be passed to `git am`. So given a pull request 162 ([https://github.com/candlepin/candlepin/pull/162](https://github.com/candlepin/candlepin/pull/162)) you can use `curl` to download the patch and then pipe it to `git am`. Once you're done reviewing, simply revert your branch back using `git reset --hard origin/master`. I added some functions to my `.bashrc` for the projects I review most often, here's the snippet:```
\# apply the given pull request from the given project as a patch
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

```

### Summary

*   `curl https://github.com/candlepin/candlepin/162.patch | git am`
*   TEST PATCH
*   `git reset --hard origin/master`