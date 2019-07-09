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