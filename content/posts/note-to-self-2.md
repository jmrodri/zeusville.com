---
title: 'Note to self'
date: Mon, 10 Aug 2009 19:43:35 +0000
draft: false
tags: [Linux]
type: post
---

Making the following changes to /etc/pulse/default.pa seems to fix the hanging audio of the flash-plugin and banshee: `load-module module-hal-detect **tsched=0**` For more information click here: [https://fedoraproject.org/wiki/Features/GlitchFreeAudio](https://fedoraproject.org/wiki/Features/GlitchFreeAudio)