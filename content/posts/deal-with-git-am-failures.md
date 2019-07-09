---
title: 'Deal with git am failures'
date: Thu, 19 Feb 2015 21:00:27 +0000
draft: false
tags: [git]
categories: [Linux, Ruby]
type: post
---

Today I needed to take my model git branch which was based off of the develop branch a week ago, and rebase it off of the master. First I did the obvious, `git rebase master` in my model branch, that yielded tons of conflicts. The conflicts were a result of commits in the develop branch being squashed when they got merged to master to keep the history clean. Instead of fixing tons of conflicts, I simply chose to take my 3 commits and create patches from them:

```


git format-patch -3 HEAD

I created a new branch off of `master` and applied my patches using `git am`.

```


git checkout master

git checkout -b model\_updates

git am ~/0001-add-rhev-params-remove-serialized-hash.patch

git am ~/0002-start-v21-of-deployments.patch

git am ~/0003-rename-columns-and-include-missing-columns.patch

Patch 0001 and ultimately 0003 applied without problems. Patch 0002 on the other hand gave me fits, I expected it, but I refused to recode the change. `git am ...` just fails when it hits a conflict. Using the trusty Google, I found this blog: [Deal with git am failures](http://www.pizzhacks.com/bugdrome/2011/10/deal-with-git-am-failures/).  I followed the instructions from that blog post:

```


git am --abort #abort the previously failed 0002 patch run

git apply ~/0002-start-v21-of-deployments.patch --reject # yield .rej files I could inspect

git add server/app/controllers/fusor/api/v2/deployments\_controller.rb # ensure changes are fine

git add server/app/controllers/fusor/api/v21/ # new files from patch

git am --resolved # tells git we're good to go, proceed.

Done! Way easier than dealing with the conflicts from the rebase. Easier than trying to recode the patch as well.


```
```
```
---
### Comments:
####
[Links 19/2/2015: Hewlett-Packard on Cumulus Linux, Previews of GNOME 3.16 Beta | Techrights](http://techrights.org/2015/02/19/cumulus-linux/ "") - <time datetime="2015-02-19 21:23:02">Feb 4, 2015</time>

\[…\] Deal with git am failures \[…\]
<hr />
