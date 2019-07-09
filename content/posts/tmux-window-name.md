---
title: 'tmux window name'
date: Thu, 30 Jan 2014 21:52:58 +0000
draft: false
tags: [Linux, Technology]
categories: [Linux, Technology]
type: post
---

Here's how I got my tmux windows to be named 'short hostname:working directory'.

Create a bash function in your `$HOME/.bashrc`.

```


settitle ()

{

    # only run this in tmux

    case "$TERM" in

        screen\*)

            # get hostname without FQDN

            H=\`hostname -s\`

            # get current directory without the full path

            D=\`basename $PWD\`

            # set title of tmux/screen window

            printf "33k$H:$D33\\\\"

            ;;

    esac

}

Then call `settitle` from your `PS1` prompt variable:

```


PS1="...(settitle)\\$ "

Here is my current prompt:

```


PS1="\[\\u@\\h \\W\\$(git branch 2> /dev/null | grep -e '\\\* ' | sed 's/^..\\(.\*\\)/{\\1}/')\]\\$(settitle)\\$ "


```
```
```