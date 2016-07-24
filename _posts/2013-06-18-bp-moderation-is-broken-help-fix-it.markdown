---
author: francesco
comments: true
date: 2013-06-18 11:32:35+00:00
layout: post
link: http://flweb.it/2013/06/bp-moderation-is-broken-help-fix-it/
slug: bp-moderation-is-broken-help-fix-it
title: BP-Moderation is broken. Help fix it!
wordpress_id: 390
categories:
- BP Moderation
---

I've been out of BuddyPress game for a while, mainly because I'm not using it on websites I curate or work on, and I was committed to other projects.

While BP-Media is maintained by other developers, I'm the only one working on this plugin and I have received emails about it not working on the latest versions of WP and BP.

I started to look into it and the **dev version should now be working** on single-site installs, Today I'll test on multisite and fix it.  I can't devote lot of time to it right now so any help, tester or developer, is appreciated.

The development version is **now on GitHub** at [https://github.com/francescolaffi/BP-Moderation](https://github.com/francescolaffi/BP-Moderation), if you are not confortable with git you can get the zipped dev version at [https://github.com/francescolaffi/BP-Moderation/archive/master.zip](https://github.com/francescolaffi/BP-Moderation/archive/master.zip).
Stable versions will be tagged in WP official svn repo.

How can you help to get it fixed?



	
  * If you use this plugin on your site** test the dev version ([zip](https://github.com/francescolaffi/BP-Moderation/archive/master.zip))** from GitHub and post the issues to [https://github.com/francescolaffi/BP-Moderation/issues](https://github.com/francescolaffi/BP-Moderation/issues) (never test it on your production website)

	
  * If you are a developer you can help to fix and improve it! Fork the GitHub repo and make a **pull request** or reach out at [francesco.laffi on skype](skype:francesco.laffi?chat) to discuss it.


I found out that BP-Moderation codebase is messed up, with logic and template mixed together and some singleton black magic to load the main classes, can't understand how it seemed a good idea when I wrote it years ago, at least is not really extensive so its workable.
I started a new **[branch 0.2](https://github.com/francescolaffi/BP-Moderation/tree/0.2) for the refactoring**, it will target PHP 5.3+, WP 3.6 and BP 1.8, maybe WP 3.5 and BP 1.7; the 0.1 branch will be compatible with BP 1.7/1.8, but won't get new feature or compatibility with later BP versions.
