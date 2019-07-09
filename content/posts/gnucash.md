---
title: 'gnucash'
date: Mon, 17 Dec 2007 05:07:44 +0000
draft: false
tags: [Family, Java, Linux]
categories: [Family, Java, Linux]
type: post
---

I'm stuck on Quicken 2002 and have thus neglected using it for almost 2 years. We've been managing the household finances the old fashioned way by hand and with the help of online banking. But I wanted to have a bit more control and a better "view" of where the money goes. So I tried using Quicken 2002 in a virtual instance of Windows XP running on VirtualBox. But Quicken 2002 is just a few years out of date! :) And the thought of upgrading it just pains me. So I set out to find financial software for Linux.

*   [GnuCash](http://www.gnucash.org)
*   [Moneydance](http://moneydance.com/)
*   [Grisbi](http://www.grisbi.org)
*   [KMyMoney](http://kmymoney2.sourceforge.net/index-home.html)
*   [CheckItOut](http://checkitout.flornet.fr/)
*   [Gnofin](http://gnofin.sourceforge.net/)
*   [Kapital](http://www.thekompany.com/products/kapital/)

I started with GnuCash but I was just completely confused with how it treats categories as accounts. The whole double entry accounting just made my eyes water. Next up I tried Moneydance. I've tried it before when I was using OS/2 but it was too "java-y". Looked out of place. Well, it still looks way out of place with the ugly Metal look and feel of swing. It was easier to get started than GnuCash as it felt more Quicken-like. But I couldn't get over how ugly the UI was. I know it shouldn't be about looks, but it was: rm -rf /opt/moneydance. I thought, "maybe there's a webapp out there that does this" which led me to CheckItOut a Ruby on Rails application. CheckItOut uses Mysql to store the data and runs using Webrick. But it was a royal pain in the butt to setup. Ruby, Rails, mysql all installed great. CheckItOut even started with a small change to database.yml. But once it was running creating a new account would cause it an error. I started to try to debug it then realized, screw this if I have to debug the app I can't trust it to keep track of my finances. So out it went. Next up? Grisbi. It looked promising. Nice GTK look and feel, pretty decent features as well. But I had a hard time using it. I kept tripping over things. So I moved on, though I left it installed just in case. Gnofin lost purely because it was an older GTK app. It was just too ugly to even bother. I didn't even get to the download point. KMyMoney2 was pretty nice. It had one of the nicer feature sets and felt pretty natural to use. I was up and running in no time. But as you probably guessed I like the GNOME look and feel, and I couldn't get past the ugly KDE candy toy look: yum remove kmymoney2. Last up was Kapital was one of the better looking apps, IMO. It was the closest to Quicken out of them all. But it wasn't open source. So it never got to the download state either. Wow, I ran out of applications. Well, I actually went back to GnuCash. I remembered what a friend told me "learn your tools". So I decided to sit down and actually learn GnuCash. After about an hour, I got a pretty good grasp on how it works and it is really a great replacement for Quicken. It has the GNOME look and feel which I love, is open source, handles all the accounts I have, imports from OFX and QIF formats as well. **WINNER:** GnuCash!