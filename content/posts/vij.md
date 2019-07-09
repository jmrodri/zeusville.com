---
title: 'vij'
date: Fri, 10 Oct 2008 21:34:35 +0000
draft: false
tags: [Linux, Technology]
categories: [Linux, Technology]
type: post
---

I've been using a bash function for launching _vim_ for quite a while. I can do things like _vij edit.jsp_ and it would find the edit.jsp and launch vim. The original version looked like this:

```
vij ()

{

find . -name "$1" -exec vim {} \\;

}

The problem would occur when there were more than one file named _edit.jsp_. Running `find . -name edit.jsp` yielded four files:

```
find . -name edit.jsp

./code/webapp/WEB-INF/pages/activationkeys/edit.jsp

./code/webapp/WEB-INF/pages/errata/edit.jsp

./code/webapp/WEB-INF/pages/channel/manage/edit.jsp

./code/webapp/WEB-INF/pages/systems/probes/edit.jsp

_vij_ would exec vim for each of the files found. This is not what I wanted, I only wanted to edit the third one. So with a little hacking I updated it to prompt me if it found more than one, so I could choose the one I wanted.

```
vij edit.jsp

Multiple matches found...

1: ./code/webapp/WEB-INF/pages/activationkeys/edit.jsp

2: ./code/webapp/WEB-INF/pages/errata/edit.jsp

3: ./code/webapp/WEB-INF/pages/kickstart/wizard/profile/advanced/edit.jsp

4: ./code/webapp/WEB-INF/pages/channel/manage/edit.jsp

5: ./code/webapp/WEB-INF/pages/systems/probes/edit.jsp

q: Quit

?

Simply add this to your $HOME/.bashrc and you'll be all set.

```
vij ()

{

    dafiles=$(find . -type f -name "$1")

    matches=$(echo $dafiles | gawk '{print NF}')

    case "$matches" in

        0)

           echo "No matches found"

           show=""

           ;;

        1)

           show=$dafiles

           ;;

        \*)

           echo

           echo "Multiple matches found..."

           i=1

           for option in $dafiles

           do

              echo "$i: $option"

              i=\`expr $i + 1\`

           done

           echo "q: Quit"

           echo

           read -p "? " ans

           if \[ "q" == "$ans" \]; then

              show=""

           else

              show=$(echo $dafiles | gawk '{print $"'"$ans"'"}')

           fi

           ;;

    esac

    if \[ "" != "$show" \]; then

       vim $show

    fi

}


```
```
```
```
---
### Comments:
#### [Victor Bogado]( "victor@bogado.net") - <time datetime="2008-10-11 16:01:38">Oct 6, 2008</time>

How about that: ``vij() { vim `find . -name "$1" -print` }`` This will open all the files and you can use :n and :prev to navigate forward and backwards.
<hr />
#### [Jay Dobies]( "jdob@redhat.com") - <time datetime="2008-10-13 08:39:20">Oct 1, 2008</time>

This is awesome. I've had the exact same script as your original version for years (except for emacs and I called it "femacs") but I never looked into fixing the multiple file issue. I'd just watch as they all popped up. I have to give this a try.
<hr />
#### [Mckenzie](http://www.puhuaclinic.com/bbs/member.php?action=profile&uid=120633 "mckenzieteasdale@gmail.com") - <time datetime="2014-09-05 06:07:26">Sep 5, 2014</time>

Wonderful goods from you, man. I have bear in mind your stuff prior to and you are simply too fantastic. I actually like what you have bought here, certainly like what you're stating and the way in which during which you are saying it. You make it enjoyable and you still take care of to keep it smart. I can't wait to learn far more from you. That is really a terrific website.
<hr />
#### [http://www.afrotainment.net/](http://www.afrotainment.net/uprofile.php?UID=123189 "savannahstephens@zoho.com") - <time datetime="2014-09-05 03:42:47">Sep 5, 2014</time>

This article is truly a good one it helps new net users, who are wishing for blogging.
<hr />
#### [Lyle](http://japanstimulus.tumblr.com/post/92053624097/raw-shea-butter "lylearrowood@web.de") - <time datetime="2014-08-31 08:00:16">Aug 0, 2014</time>

When I initially commented I seem to have clicked on the -Notify me when new comments are added- checkbox and now every time a comment is added I receive 4 emails with the same comment. Is there a way you are able to remove me from that service? Kudos!
<hr />
