---
title: 'remote virt-manager access via SSH'
date: Tue, 13 Jan 2015 02:09:07 +0000
draft: false
tags: [Personal]
categories: [Personal]
type: post
---

For the most part I always used virt-manager locally to manage my development guests. There was a nice article, sorry it escapes me right now, on how to setup a policy to avoid entering the password locally a bazillion times.

When I worked from home using virt-manager to remotely manage my guests on my workstation was unbearable. Why? Because it meant entering the root password a bazillion times. After years of suffering through this, TODAY! I finally found this really old Fedora documentation:

[Virtualization Guide](http://docs.fedoraproject.org/en-US/Fedora/13/html/Virtualization_Guide/chap-Virtualization-Remote_management_of_virtualized_guests.html)

What's the secret? SSH-KEYS! UGH! trivial. All this time all I had to do was setup my keys so I could login to the box. This removed the necessity for entering the root password a BAZILLION time. Now I enter my passphrase once and done. UGH! really so simple.

So if you've been trying to use virt-manager to remotely manage your guests and having to enter the password in that tiny @$$ password box, try setting up your ssh-keys correctly.