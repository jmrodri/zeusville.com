---
title: 'Fun with cli file transformation'
date: Tue, 24 Mar 2015 01:55:56 +0000
draft: false
tags: [awk, cli, grep, linux, tr]
categories: [Linux, Technology]
type: post
---

I used the Wake County property tax page to get a list of all of the homes in our neighborhood. I pasted that into a spreadsheet. The Proper and Proper last columns are actually cells using the `=PROPER()` function. It takes the given cell and converts it from all upper case to proper case. The resulting list looks like this:

Address

Street

Last name

Owners

Proper

Proper last

E-mail

123

SCRABBLES DR

JONES

FRED

Fred

Jones

neighbor1@email.com

456

SCRABBLES DR

BONES

WILMA

Wilma

Bones

neighbor2@eahoo.com

I probably could've done this whole thing without using the spreadsheet or the `=PROPER()` function but it was easier considering the original data came from a table. I then exported that as a [CSV](http://en.wikipedia.org/wiki/Comma-separated_values) file.

```


Address,Street,Last name,Owners,Proper,Proper last,E-mail,

123,SCRABBLES DR,JONES,FRED,Fred,Jones,neighbor1@email.com,

456,SCRABBLES DR,BONES,WILMA,Wilma,Bones,neighbor2@eahoo.com,

What I'm trying to do is get a list with the following format:

```
"First Lastname" <emailaddress@domain.com>, "First Lastname" <email2@domain.com>
```

I did it with the following command line. The trickiest was getting awk to print out the double quotes uses "\\42" 

```


cat neighbors.csv | grep -v ^Address | awk -F , '{print "\\42"$5" "$6"\\42 <"$7">,"}' | grep -v "<>" | tr '\\n' ' ' > full-list.txt

I then copy and pasted the resulting file contents into the "Direct add members" feature. The one tidbit that I had to do was only copy and paste 10 addresses at once. I probably could've updated the above script to do that for me. But by this point I got 90% of what I needed so I just split the rest by hand.


```
```
---
### Comments:
#### 
[jmrodri](http://zeusville.wordpress.com/ "jmrodri@gmail.com") - <time datetime="2015-03-24 10:24:06">Mar 2, 2015</time>

Thanks for the tip Rich. looks like the package is simply called `csv` on the Fedora 21 repos.
<hr />
#### 
[rich](http:// "rich@annexia.org") - <time datetime="2015-03-24 07:06:26">Mar 2, 2015</time>

Please don't use awk to parse CSV files. It's not even remotely safe. Use a program like `csvtool` instead (it's in Fedora).
<hr />
