---
author: francesco
comments: true
date: 2010-05-10 09:32:15+00:00
layout: post
link: http://flweb.it/2010/05/add-confirm-email-field-in-buddypress-signup-page/
slug: add-confirm-email-field-in-buddypress-signup-page
title: Add confirm email field in BuddyPress signup page
wordpress_id: 124
categories:
- Hacks &amp; Tutorials
tags:
- BP UI
- signup
---

Some time ago I've seen from the server log of a client buddypress site that lot of registration email were bouncing back. It was clear that for the most part they were mispelled and the client decided it was better to add another registration field then loosing a good amount of new members (bouncing emails was 4-5% of successful registrations).

As I [read on the forum](http://buddypress.org/community/groups/how-to-and-troubleshooting/forum/topic/verify-email-before-register/) that other people were asking for email confirm field, I decided to inaugurate a new category for [Hacks & Tutorials](http://flweb.it/category/coding/hacks-and-tutorials/) with this little snipped that add another email field and check it.

Paste this code in your bp-custom.php file or in your custome theme function.php. I tested it only with that site, but it should work with every buddypress site that use the default theme or a child of it. If you have problem ask detalied question with all your software versions, your site url and any error message.

[php]function registration_add_email_confirm(){ ?>
	<?php do_action( 'bp_signup_email_first_errors' ); ?>
	<input type="text" name="signup_email_first" id="signup_email_first" value="<?php
	echo empty($_POST['signup_email_first'])?'':$_POST['signup_email_first']; ?>" />
	<label>Confirm Email <?php _e( '(required)', 'buddypress' ); ?></label>
	<?php do_action( 'bp_signup_email_second_errors' ); ?>
<?php }
add_action('bp_signup_email_errors', 'registration_add_email_confirm',20);

function registration_check_email_confirm(){
	global $bp;

	//buddypress check error in signup_email that is the second field, so we unset that error if any and check both email fields
	unset($bp->signup->errors['signup_email']);

	//check if email address is correct and set an error message for the first field if any
	$account_details = bp_core_validate_user_signup( $_POST['signup_username'], $_POST['signup_email_first'] );
	if ( !empty( $account_details['errors']->errors['user_email'] ) )
		$bp->signup->errors['signup_email_first'] = $account_details['errors']->errors['user_email'][0];

	//if first email field is not empty we check the second one
	if (!empty( $_POST['signup_email_first'] ) ){
		//first field not empty and second field empty
		if(empty( $_POST['signup_email'] ))
			$bp->signup->errors['signup_email_second'] = 'Please make sure you enter your email twice';
		//both fields not empty but differents
		elseif($_POST['signup_email'] != $_POST['signup_email_first'] )
			$bp->signup->errors['signup_email_second'] = 'The emails you entered do not match.';
	}
}
add_action('bp_signup_validate', 'registration_check_email_confirm');[/php]

﻿WordPress and BuddyPress have a very good hook system so they can be easily customized with short snippets. Is there some other widely useful customization needed?
