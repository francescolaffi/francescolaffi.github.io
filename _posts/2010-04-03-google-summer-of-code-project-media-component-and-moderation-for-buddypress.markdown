---
author: francesco
comments: true
date: 2010-04-03 12:56:00+00:00
layout: post
link: http://flweb.it/2010/04/google-summer-of-code-project-media-component-and-moderation-for-buddypress/
slug: google-summer-of-code-project-media-component-and-moderation-for-buddypress
title: 'Google Summer of Code project: media component and moderation for BuddyPress'
wordpress_id: 101
categories:
- Coding
tags:
- GSoC
- media
- moderation
---

**UPDATE:** This GSoC proj has been accepted! :D I'll post more information as soon as I define the details with my mentors.

I'm going to apply for a Google Summer of Code (GSoC) project related to BuddyPress, I have two ideas for it: extending the bp-album plugin to a **complete media component** plugin and coding a **moderation plugin**.


### Media component


I'm already working with foxly to add multiple album, album for groups, flexible taxonomy, member tags (a beta will be ready soon). When this features are tested and released in a stable version, we will work on multiple uploads, widgets, sitewide directory, shortcodes for blog posts. All these features are not part of the GSoC project.

The part of my GSoC proj related to media is mainly extending bp-album to support every kind of media file and upload from remote locations. Remote url could be either a media file or an oEmbed enabled page.

Multimedia capability will be accomplished abstracting the media type and adding the support for media modules. Each module can describe how to display the media files it supports, how to generate thumbs or to use a default thumb. It can also hook in bp-album functions to change the way they handle media files.

I'll write some basic modules (pics, video, audio) and a detailed documentation on the modules API. Then community could code modules for every kind of media (flash, pdfs, documents, code scripts, ...).


### Moderation component


Site admins can already edit or delete every content in a BP community, but analyzing every content posted could be a crazy/impossible work in big communities. This plugin use crowdsourcing to help site admins finding contents to moderate.

It adds a "report this" link to every posted content in the site, so members can easily report contents to admins. Admins can then see all the reported contents in an organized table in the wp backend, order/filter by the number of times the content has been reported, the component that have generated the content, the member who posted the content, etc. Then admins can take action on that content (ignore it, delete, mark the content author as spammer).

Another table show members, how many posts from them have been reported/moderated, how many posts have they reported and moderated from admin. So admins can easily find bad/good members and take action on them (mark as spammer, thanks them).


### Timing


Accepted projects are announced on April 26, then Google timeline suggest a month of 'community bonding' and starting coding on May 24. Suggested 'pencil down' date is August 9, projects must be completed before August 16.

What happens if my project is not accepted? I won't discard it, but I can't affirm that I'll have the time to work on it, or give any accurate timing. If it is accepted Google will give me a stipend to complete the project, so I can afford not accepting paid works and I'll not look for a summer job; otherwise I'll need to find some works for this summer and I don't know how much time I'll have to work on this.

Hope you like my ideas, feedback in comments is appreciated.
