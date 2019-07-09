---
title: 'git branch in shell prompt'
date: Wed, 19 May 2010 13:52:16 +0000
draft: false
tags: [git prompt bash]
categories: [Linux, Technology]
type: post
---

I've used this prompt for quite some time but realized I never blogged about it :)

As a git user I tend to work in a few branches at a time. Unlike subversion where you typically have a separate directory for each branch, with git branches update the working directory. So it is easy to get lost when you have more than one branch. Sure you can do

```
git branch
```and```
git branch -r
```but this can be invasive when you could easily glance at your shell prompt.

In bash (is there really any other shell?), I updated my prompt to show the current branch:

```
PS1="\[\\u@\\h \\W\\$(git branch 2> /dev/null | grep -e '\\\* ' | sed 's/^..\\(.\*\\)/{\\1}/')\]\\$ "

This make the prompt look like this:

```
\[jmrodri@firebird sm-photo-tool{master}\]$
```
```
---
### Comments:
#### [Clint Savage](http://sexysexypenguins.com "herlo@fedoraproject.org") - <time datetime="2010-05-19 11:05:46">May 3, 2010</time>

I'd actually suggest that you have a look at the git-completion package. They have executables for exactly this purpose. The one you are looking for in this case: \_git\_ps1. http://blog.bitfluent.com/post/27983389/git-utilities-you-cant-live-without Cheers, Clint
<hr />
#### [Stick]( "stick@miscellaneous.net") - <time datetime="2010-05-19 10:40:57">May 3, 2010</time>

I use PS1='\[\\u@\\h \\W$(\_\_git\_ps1 "(%s)")\]\\$ ' and then with the bash\_completion stuff for git that provides the \_\_git\_ps1 function. the bash\_completion git file (which gives a whole slew of fun stuff) should be in the git source under contrib or something. \_\_git\_ps1 () { local g="$(git rev-parse --git-dir 2>/dev/null)" if \[ -n "$g" \]; then local r local b if \[ -d "$g/rebase-apply" \] then if test -f "$g/rebase-apply/rebasing" then r="|REBASE" elif test -f "$g/rebase-apply/applying" then r="|AM" else r="|AM/REBASE" fi b="$(git symbolic-ref HEAD 2>/dev/null)" elif \[ -f "$g/rebase-merge/interactive" \] then r="|REBASE-i" b="$(cat "$g/rebase-merge/head-name")" elif \[ -d "$g/rebase-merge" \] then r="|REBASE-m" b="$(cat "$g/rebase-merge/head-name")" elif \[ -f "$g/MERGE\_HEAD" \] then r="|MERGING" b="$(git symbolic-ref HEAD 2>/dev/null)" else if \[ -f "$g/BISECT\_LOG" \] then r="|BISECTING" fi if ! b="$(git symbolic-ref HEAD 2>/dev/null)" then if ! b="$(git describe --exact-match HEAD 2>/dev/null)" then b="$(cut -c1-7 "$g/HEAD")..." fi fi fi if \[ -n "$1" \]; then printf "$1" "${b##refs/heads/}$r" else printf " (%s)" "${b##refs/heads/}$r" fi fi }
<hr />
#### [Juanjo](http://rambleon.usebox.net/ "reidrac@usebox.net") - <time datetime="2010-05-19 10:18:15">May 3, 2010</time>

Just wondering: every time the shell shows the prompt, git branch gets executed? That's the main reason I don't like to mess too much with the shell prompt, but I may be wrong...
<hr />
#### [wwoods](http://wwoods.fedorapeople.org/ "wwoods@redhat.com") - <time datetime="2010-05-19 12:45:34">May 3, 2010</time>

Not just 'git branch' - also 'grep' and 'sed'. Three fork/execs per prompt. Blarg! String manipulation inside bash isn't too hard. You can do something like: function git\_branch\_for\_cwd() { b=$(git symbolic-ref HEAD 2>/dev/null); \[ "$b" \] && echo "{${b##\*/}}"; } PS1="\[\\u@\\h \\W\\$(git\_branch\_for\_cwd)\]\\$ " which at least drops the grep and sed. (echo is a shell builtin, so no fork/exec there). But yeah. Try git-completion, where someone's already done the work for you.
<hr />
#### [Karsten 'quaid' Wade]( "quaid@iquaid.org") - <time datetime="2010-05-19 17:21:38">May 3, 2010</time>

Strangely enough, I had this exact same conversation via my own blog last November: http://iquaid.org/2009/11/12/updated-technique-for-seeing-git-and-directory-status-in-bash-prompt/ ... with the result that I know happily use git-completion. :)
<hr />
#### [Ben Boeckel: VCS in Shell Prompt &laquo; Febuntoo News Generator](http://febuntoo.com/ben-boeckel-vcs-in-shell-prompt.html "") - <time datetime="2010-05-23 11:26:03">May 0, 2010</time>

\[...\] Rodriguez recently posted about putting git information into his shell prompt with the mention that bash is the one and only \[...\]
<hr />
#### [Richard Foley](http://www.rfi.net "richard.foley@rfi.net") - <time datetime="2010-11-19 06:08:55">Nov 5, 2010</time>

Hi wwoods, That's nice, in some environments it's not possible to get git-completion installed (easily) and it's good to see a lightweight solution using the extant tools.
<hr />
