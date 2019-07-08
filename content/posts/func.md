---
title: 'I''ve got the Func'
date: Tue, 02 Oct 2007 03:25:17 +0000
draft: false
tags: [func, func python linux, python]
type: post
---

[Func](https://hosted.fedoraproject.org/projects/func/wiki) is an interesting project that solves some important problems.

*   Have you ever tried to manage a large number of systems with SSH? Have you wanted a better way?
*   Have you wanted a way to audit all of your remote commands on all of your systems?
*   Tired of writing shell scripts and parsing command output?
*   Are you fed up with CIM, WBEM, and complicated systems that prevent you from doing /real/ work?
*   Well have we got a solution for you. It's Func.

It was recently [released](http://www.michaeldehaan.net/?p=379) after only **two** weeks of development. That to me is amazing, how a few people can get together and accomplish so much. Kudos! I wanted to try out a simple feature: get the status of my httpd process, and bounce it. Here's a summary of what I did:

*   install func rpm on [RHEL](http://www.redhat.com/rhel/) 4 (my minion)
*   install func rpm on [Fedora](http://fedoraproject.org/) Core 6 (my overlord)
*   create a cert for the minion
*   start up the certmaster on the overlord box
*   start up funcd on the minion box
*   run command
*   DONE

For more information on Func setup see the wiki: [https://hosted.fedoraproject.org/projects/func/wiki/InstallAndSetupGuide](https://hosted.fedoraproject.org/projects/func/wiki/InstallAndSetupGuide) Here's a screenshot of my overlord (top window) run /sbin/service status httpd and /sbin/service restart httpd on the minion (bottom two windows). The bottom most window shows the funcd log in DEBUG mode and the middle window is the httpd error\_log. [![Func test](http://zeusville.files.wordpress.com/2007/10/func_demo.png)](http://zeusville.files.wordpress.com/2007/10/func_demo.png "Func test") That was great. Now I can setup my kickstart files to install func on all my machines so I can control them with func. The Func wiki covers how to [provision](https://hosted.fedoraproject.org/projects/func/wiki/IntegratingWithProvisioning) with [Cobbler](http://cobbler.et.redhat.com/).