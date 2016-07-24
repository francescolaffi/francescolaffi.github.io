---
author: francesco
comments: true
date: 2010-05-22 08:25:32+00:00
layout: post
link: http://flweb.it/2010/05/some-thoughts-on-buddypress-moderation/
slug: some-thoughts-on-buddypress-moderation
title: Some thoughts on BuddyPress Moderation
wordpress_id: 168
categories:
- BP Moderation
tags:
- dev thoughts
- gsoc2010
---

Here we have a draft of how I think to make BuddyPress Moderation work and its datamodel.


### Content types


User-generated contents in a buddypress community are not limited to few content types but can be virtually anything, so this plugin needs to be able differentiate them and have a function to add custom content during page loading (before page is generated).

Each component that lets users generate contents differentiate them with an ID (actually there could be 2 ids, i.e. blog posts in a network install need blog id and post id to be identified); bp-moderation can use those ids to distinguish among contents of the same type, but it also need to store item_type.


### Relationship Content <-> Activity


An activity is a content? Actually it isn't. An activity is a pointer to a content, that could be a status, a blog/forum post, etc...

In a single content page or in a specified content type loop, the function that generates the report link is hooked to a content type specific hook, so it's easy to know which is the content type.

Instead the activity loop displays a great number of different content types, so it's necessary to have a map that relates activities 'type' to bp-moderation 'item_type' (each item_type could have more than one activity type mapped to it).


### Contents vs Actions


Not all activities correspond to a user-generated content, there are also action activities, for example a new user, a new friendship, a user that become member of a group; imho does not make sense to flag actions as inappropriate, so I'll not create content types mapped to action activities, but it's possible to do it as with any other custom content type.


### Data Model


This is the draft of the database schema. Each content can be flagged from different user more than one time, so two tables are needed, contents table contains info about contents and their status, and flags table contains who and when flagged a content.

[![](/app/uploads/2010/05/schema2.png)](/app/uploads/2010/05/schema2.png)

_status_ could be '_new_' (if admin still haven't taken any action), '_moderated_' (admin moderated the content), '_ignored_' (admin said that content is ok).

_item_owner_id_ and _reporter_id_ are the id (as it is in wp_user table) of user that generated the content and the id of the user that flagged it.
