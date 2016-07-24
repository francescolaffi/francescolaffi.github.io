---
author: francesco
comments: true
date: 2013-10-18 12:09:29+00:00
layout: post
link: http://flweb.it/2013/10/ghost-just-a-blogging-platform-in-node-js/
slug: ghost-just-a-blogging-platform-in-node-js
title: 'Ghost: just a blogging platform in node.js'
wordpress_id: 472
categories:
- General
tags:
- dev thoughts
- ghost
- nodejs
---

I'm checking out Ghost, a newborn **node.js blogging platform focused on the user experience**, these are my first impressions, as user and developer.


![Ghost-Logo-on-White](/app/uploads/2013/10/Ghost-Logo-on-White-1024x328.png)





## Installation


The [installation instructions](http://docs.ghost.org/installation/) are easy, especially for test environments, since nodejs doesn't need a webserver like nginx or apache, and Ghost can use **sqlite** as db, so the simplest complete stack to run Ghost is just nodejs.
[![](/app/uploads/2013/10/Ghostintheshellposter.jpg)](http://en.wikipedia.org/wiki/Ghost_in_the_Shell_(film))
OT: I can't work from in the terminal with something named Ghost and not even mention "[Ghost in the Shell](http://en.wikipedia.org/wiki/Ghost_in_the_Shell_(film))", one of my favorite sci-fi anime films. If you don't know it you should definitely watch it!

I spinned up a Ghost workbench at [ghost.flweb.it](http://ghost.flweb.it/) on the same vps that hosts this blog, a couple of other WP sites and some test projects, in a Digital Ocean droplet (if you are looking for an easy vps for small project Digital Ocean is great, you can use [this link](https://www.digitalocean.com/?refcode=3e8e36beebe5) with my ref code)

Installation on a **production** oriented environment can be more elaborate, i.e. in my vps I already have **nginx** on port 80, so nginx is set up to proxy the connection to the unix socket Ghost is listening to, nginx can also be used to serve static files directly; to ensure that Ghost stays alive I use **forever**, configured as an upstart service. I use vagrant+chef to configure this server and its all on github: [https://github.com/francescolaffi/vagrant-chef-dev-box](https://github.com/francescolaffi/vagrant-chef-dev-box). For heavy usage you'll also need a standalone db, but for me sqlite is enough.


## Features, interfaces and experience


Ghost is very much a **work-in-progress**, the feature set is minimal for now, but you can already appreciate the admin interface simplicity. You can get a taste of the current and future features at [ghost.org/features](http://ghost.org/features/) and [github.com/TryGhost/Ghost/wiki/Planned-Features](https://github.com/TryGhost/Ghost/wiki/Planned-Features). The aim is a lean non-bloated blogging platform and I appreciate it.

I really enjoy the clean and slick writing screen with **markdown syntax** and **live preview**. It's easy to see the effort for experience and details, i.e. it has built-in support for saving articles with **cmd-s**, it's something a lot of more mature projects don't support natively.




## Developing on Ghost


Node.js uses different paradigms compared to other popular web languages like php and ruby, it's not trivial to structure async code in big project and it risks to be a callback hell. Ghost uses [promises](http://promises-aplus.github.io/promises-spec/) with [whenjs](https://github.com/cujojs/when) to 'linearize' the control flow, it also use popular building blocks like [express](http://expressjs.com/) framework, [bookshelf](http://bookshelfjs.org/) orm and [handlebars](http://handlebarsjs.com/) templating. It's looking good, some parts still looks messy, but at this stage is understandable.

For **contributing to the core** there are already lot of [guidelines and tips](https://github.com/TryGhost/Ghost/blob/master/CONTRIBUTING.md), the [CLA](https://github.com/TryGhost/Ghost/blob/master/CONTRIBUTING.md#contributor-license-agreement) is pretty standard and not shady. At this stage the core is evolving quickly, so maybe its not practical for casual contribution; the dev documentation is lacking, there is a [roadmap for milestones](https://github.com/TryGhost/Ghost/wiki/Roadmap) and [releases](https://github.com/TryGhost/Ghost/wiki/Pre-release-Roadmap), but is not very clear on the implementations and code architecture choices.
![handlebars logo](/app/uploads/2013/10/handlebars-300x174.png)
**Theme development** leverages handlebars template, it looks easy and clean, it's [documented here](http://docs.ghost.org/themes/). Right now the theme features are limited and themes are just a collection of views and assets.

The **plugin API** is WIP and still not ready, I gave it a shot anyway and I wrote a [ghost plugin for syntax highliting](https://github.com/francescolaffi/ghost-prism-plugin/). I'm looking forward to a more powerful plugin framework.


## WordPress vs Ghost


Different products for **different targets**, WordPress is more than ever a complete CMS and a publishing platform, Ghost aim to be a lean platform for blogging.

For many WP sites Ghost is not a competitor, for simple blogs it sure is tempting. I also see it as a valid **alternative to static sites generators** as jekyll for some usages: its still a no frills solution that doesn't require much infrastructure, but it's much more convenient to use.

When is a bit more mature I might even use it here on this blog :)
