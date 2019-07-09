---
title: 'Changing dates in Thunderbird'
date: Sun, 03 Apr 2005 13:32:05 +0000
draft: false
tags: [Personal]
categories: [Personal]
type: post
---

Apart from that: the nsIScriptableDateFormat user\_prefs should work in

TB, too

// ---------- date format (see nsIScriptableDateFormat.idl)

[http://lxr.mozilla.org/mozilla/source/intl/locale/idl/nsIScriptableDateFormat.idl#79](http://lxr.mozilla.org/mozilla/source/intl/locale/idl/nsIScriptableDateFormat.idl#79)

user\_pref("mail.ui.display.dateformat.default", 2); // 31.12.1999 23:59

user\_pref("mail.ui.display.dateformat.thisweek", 4); // Wed 23:56

user\_pref("mail.ui.display.dateformat.today", 0); // 23:53