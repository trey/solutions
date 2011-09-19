---
date: 2008-06-14 22:22:17
title: Flagging a Post as Outdated Using WordPress Custom Fields
layout: post
wordpress_url: http://solutions.treypiepmeier.com/2008/06/using-wordpress-custom-fields/
---
If you write a blog whose primary purpose is to help people find and remember information (mostly myself in this case), then it's probably a good idea to flag certain posts as out-of-date so as not to mislead people who are on a quest for knowledge.  That is, of course, if you know it's outdated.  Maybe [someone will tell you](/2006/12/04/rails-migration-data-types/#comment-16966).

In any case, here's how you can do it using Custom Fields in WordPress.

Find a post that's out of date and edit it.  Down towards the bottom of the page, there's a section labeled Custom Fields, click it to open it, and enter something like this:

![Create a Custom Field](/wp-content/uploads/2008/06/create_custom_field.png)

Use whatever name you want for the `key` and `value`, but be sure to change the related fields in the other places I'm about to mention.

I want the notice to show up on the post's permalink page, so in `single.php`, I put this right after the start of 'the loop':

	$status = get_post_meta($post->ID, 'status', true);

As you can probably guess, that just grabs the content for the 'status' key for the current post and stores it in the variable `$status`.  Easy.  If the post doesn't have the value, the `get_post_meta` tag is nice enough to fail quietly (as far as I can tell).

Now that you have this very valuable information, you can change CSS, add a warning message, or whatever your little heart desires.

For example:

	if ($status == 'outdated') include (TEMPLATEPATH . '/outdated.php');

### Sources
- I got the idea from [Bryan Veloso](http://bryanveloso.com/)'s [Avalonstar](http://avalonstar.com/blog/2007/may/4/my-reasons-django/)
- [WordPress Codex / get_post_meta](http://codex.wordpress.org/Function_Reference/get_post_meta)
- [WordPress Codex / Using Custom Fields](http://codex.wordpress.org/Using_Custom_Fields)
