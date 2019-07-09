---
title: 'Sendmail & local ISP'
date: Sat, 24 Jul 2004 23:50:27 +0000
draft: false
tags: [Linux]
categories: [Linux]
type: post
---

I've always had my machines attempt to send me email at my isp address but they always got bounced back.

So I finally set out to determine how to get sendmail to use my ISPs smtp server to send out email. And it turns out be a trivial task, but one I will document here for others to use:

You must be root to do this and stop sendmail:

```


su

/sbin/service sendmail stop

Always backup your configuration files otherwise, don't come crying to me when your sendmail.cf is 0 bytes.

```


cd /etc/mail

cp sendmail.cf sendmail\_cf.bak

cp sendmail.mc sendmail\_mc.bak

Edit sendmail.mc (uncomment or add)

```


define(\`SMART\_HOST',\`smtp.your.isp.com')

Ensure you have sendmail-cf installed, otherwise install it.

```


rpm -q sendmail-cf

yum -y install sendmail-cf

Now rebuild sendmail.cf and restart sendmail.

```


m4 sendmail.mc > sendmail.cf

/sbin/service sendmail start


```
```
```
```
```
---
### Comments:
#### 
[Damian Murphy](http://blog.murf.org "spam@murf.org") - <time datetime="2004-07-25 20:36:31">Jul 0, 2004</time>

At the risk of getting flamed for going beyond the command line - I can thoroughly recommend webmin (http://www.webmin.com) - it's interface for sendmail configuration is really quite good.
<hr />
#### 
[Jesus M. Rodriguez](http://www.jroller.com/page/jmrodri "jmrodri@nc.rr.com") - <time datetime="2004-07-26 16:18:30">Jul 1, 2004</time>

No one should ever get flamed for not using the command line. I'd be perfectly happy if every admin task was available through a UI in Linux. And I think it would make it even more popular for the home user.
<hr />
#### 
[Chris]( "") - <time datetime="2006-03-07 11:59:14">Mar 2, 2006</time>

Thanks for this. Short & to the point.
<hr />
