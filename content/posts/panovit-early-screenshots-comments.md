---
title: 'panovit early screenshots'
date: Tue, 10 Aug 2010 03:03:48 +0000
draft: false
tags: [Java, Linux, Technology]
---


#### 
[broman]( "taalgaard@yahoo.com") - <time datetime="2010-08-11 22:42:04">Aug 3, 2010</time>

Nice start. I'm just beginning to dabble in HME myself. I downloaded your code and played around a little. Here's some code that will capture the input from the keyboard screen, save it, then make a new item on the first screen. public boolean handleEvent(HmeEvent event) { System.out.println("opcode: " + event.getOpCode()); System.out.println("id: " + event.getID()); if (event instanceof KeyboardEvent) { System.out.println("value: " + ((KeyboardEvent)event).getValue()); userInputFromKeyboard = ((KeyboardEvent)event).getValue(); } if(event.getOpCode()==7202 && userInputFromKeyboard!=null && userInputFromKeyboard !=""){ System.out.println("newmenuitem: " + ((KeyboardEvent)event).getValue()); sl.add(userInputFromKeyboard); userInputFromKeyboard = ""; } return super.handleEvent(event); }
<hr />
