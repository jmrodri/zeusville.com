---
title: 'Candlepin 0.4.16 released.'
date: Thu, 15 Sep 2011 19:35:13 +0000
draft: false
tags: [Java, Linux, python, Technology]
categories: [Java, Linux, python, Technology]
type: post
---

Another sprint gone by and another release of Candlepin for your enjoyment. Candlepin 0.4.16 is ready. You can get the bits at: [http://repos.fedorapeople.org/repos/candlepin/candlepin/](http://repos.fedorapeople.org/repos/candlepin/candlepin/) Make sure you read over the [Setup Guide](https://fedorahosted.org/candlepin/wiki/Setup), which is located at [https://fedorahosted.org/candlepin/wiki/Setup](https://fedorahosted.org/candlepin/wiki/Setup) For more information on Candlepin, please visit [our project page](http://candlepinproject.org/). **Features & Enhancements** **_client_**

*   A number of GUI changes
    *   Center the machine type column header
    *   Move quantity column to the end
    *   Center the Arch column header
    *   Center tree view table properties
    *   Add '\* Click to Adjust Quantity' label to places allowing editable subscription quantity
    *   New icons for red/green
    *   Add virt\_only attribute to subscription detail pane
    *   Display subscription assistant's subscriptions as a tree
    *   Double click or button press (enter, return, space) on row will expand/collapse row
    *   Update to All Available Subscriptions tab to put stacked subscriptions under parent node
    *   Moved multi-entitlement column (\*) next to the quantity column
    *   Made the contract selector a little wider so all columns were visible (no manual resize)
*   Initial work done for the healing feature
    *   Changes to rhsmcertd to support healing frequency (part I)
    *   Add autoheal option to certmgr.py
    *   Only autoheal when required
    *   Use server-side consumer autoheal flag
*   Misc items
    *   Update the strings and the remote server location
    *   Make "make stylish" run all the checks, make whitespace "pop"
    *   Update translations
    *   managerlib was expecting a single ent\_cert, but we return a list
    *   Add a "refresh" method to cert\_sorter
    *   Add a require\_connection callback to commands

**_server_**

*   upgraded to [RESTEasy](http://www.jboss.org/resteasy) 2.2.1GA
*   export virt entitlements to non-candlepin consumers
*   refactored pinsetter to work in clustering mode
*   add new api to query jobs by owner, principal, consumer uuid

**Bugs fixed**

707641

CLI auto-subscribe tries to re-use basic auth credentials

712047

yum prints non-error messages when running in quiet mode

718052

Remove owner from consumer resource return codes. Only use the term org.

730020

Change the help text to show that config can list or set changes

731577

API to query jobs by owner, principal, consumer uuid.

731996

SQL Error when using REST query for events

732538

Disallow the relationship between a 'person' pool and an activation key

734174

Add missing produces annotations for role resource.

734880

Handle bundled certs in the installed produict status.

734606

ImportFileExtractor now creates cert/key files based on serial number of the cert

735087

If quartz is in clustered mode, we shouldn't schedule any jobs.

735226

Importing should fail without a valid key and cert

735338

Subscription Manager CLI tool does not allow unsubscribe when not registered.

735695

add support for multiple config "--remove" options via cli

736166

move certs from subscription-manager to python-rhsm

736784

config --remove add config property to rhsm.conf if it doesn't exist.

737841

Handle dates beyond 2038 on 32-bit systems.