---
title: 'Greasemonkey'
date: Fri, 14 Dec 2007 18:28:45 +0000
draft: false
tags: [Technology]
type: post
---

I'm late to the game as [Greasemonkey](https://addons.mozilla.org/en-US/firefox/addon/748) has been around for quite a while. But today I decided to write my own script. I'm using the [Neutronium GTK theme](http://gnome-look.org/content/show.php/Neutronium+Unity?content=59189)and bugzilla.redhat.com had white text on yellow buttons. So I wrote a script to change the colors. It's not very pretty but it works for me.```
// ==UserScript==
// @name            Bugzilla Style
// @namespace       http://zeusville.wordpress.com
// @description     Changes the color of the yellow buttons
// @include         https://bugzilla.redhat.com/\*
// @include         http://bugzilla.redhat.com/\*
// ==/UserScript==

var element;
var inputs = document.getElementsByTagName('input');
for (var i = 0; i < inputs.length; i++) {
    element = inputs\[i\];
    if (element.type == 'text' || element.type == 'checkbox' ||
        element.type == 'radio') {

        element.style.background = "#141414";
    }
    else if (element.type == 'submit') {
        element.style.background = "#313131";
    }
}

var elements = document.getElementsByTagName('select');
for (var i = 0; i < elements.length; i++) {
    element = elements\[i\];
    element.style.background = "#141414";
}

elements = document.getElementsByTagName('textarea');
for (var i = 0; i < elements.length; i++) {
    element = elements\[i\];
    element.style.background = "#141414";
}
```