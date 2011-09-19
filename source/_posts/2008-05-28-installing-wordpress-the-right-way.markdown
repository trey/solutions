---
date: 2008-05-28 16:25:32
title: Installing WordPress The Right Way (revised)
layout: post
wordpress_url: http://solutions.treypiepmeier.com/2008/05/installing-wordpress-the-right-way/
---
Keep WordPress core files entirely separate from your content (themes, plugins, uploads).

There are a couple of ways to keep your WordPress install up-to-date.  The easiest way is to install it as an `svn:external`.  In the root of your (Subversioned) site:

	svn propedit svn:externals .

Then paste in:

	wordpress http://svn.automattic.com/wordpress/tags/[current_tag_number]

Replacing `[current_tag_number]` with the current tag number (check [wordpress.org/download/](http://wordpress.org/download/) to see the latest).  Alternately, you can just [download WordPress](http://wordpress.org/download/) and put it in a `wordpress` folder (or `wp` or whatever you prefer) in the root of your site.

Now copy the default `wp-content` folder from the fresh copy of WordPress to the root of your site:

	cp -R wordpress/wp-content .

Delete the existing `.svn` folders from your fresh new `wp-content`.

	cd wp-content
	rm -rf `find . -type d -name .svn`

Now create your `wp-config.php`

	cd ..
	cp wordpress/wp-config-sample.php wp-config.php

Edit the file and add your database info.  While you're in there, add these settings to the top of the file:

	// Custom wp-content folder: 
	define('WP_CONTENT_DIR', $_SERVER['DOCUMENT_ROOT'] . '/wp-content' );
	define('WP_CONTENT_URL', 'http://' . $_SERVER['SERVER_NAME'] . '/wp-content');

	define('WP_HOME', 'http://' . $_SERVER['SERVER_NAME'] . '');
	define('WP_SITEURL', 'http://' . $_SERVER['SERVER_NAME'] . '/wordpress');

Those settings do a number of cool things.  First, you're allowing WordPress to use your fresh copy of `wp-content` in the root of your site instead of the one that lives inside of the `wordpress` folder.  Second, you're specifically setting some WordPress variables that are normally defined in its database in PHP, so that you won't have to readjust your settings between development (on your local machine) and where it lives in the wild.  Third, you're telling WordPress where to find it's core files since you've put them in a subfolder (`/wordpress`).

Now copy `index.php` from WordPress to the root of your site:

	cp wordpress/index.php .

Edit the file and change the line that says:

	require('./wp-blog-header.php');

To this:

	require('./wordpress/wp-blog-header.php');

If you want fancy URLs (you do), create an `.htaccess` file:

	touch .htaccess
	chmod 666 .htaccess

Duplicate the `default` theme:

	cp -R wp-content/themes/default wp-content/themes/[your_new_theme]

Replacing `[your_new_theme]` with what you want your new theme to be called.

### Bonus: keep Akismet as an svn:external for automatic updates from [Automattic](http://automattic.com/).

	cd wp-content/plugins/
	rm -rf akismet

Or, if you're already committed your code:

	svn rm akismet
	svn ci -m "Moving Akismet to external."

Then setup the external link:

	svn propedit svn:externals .

Paste in:

	akismet http://plugins.svn.wordpress.org/akismet/trunk/

### That's it.

Now commit your code and get to it.  If you get lost, check out [wp-template](http://wp-template.googlecode.com/) for an example.

### Updating WordPress

	svn propedit svn:externals .

Change the tag number, then `svn update` and you're good to go.

If you're not using `svn:externals`, just dump a new copy of WordPress over the one that's already in `/wordpress`.  There's no way you can hurt your existing content, because that's all in the `/wp-content` folder in the root of your site.

### Sources

- [Installing/Updating WordPress with Subversion](http://codex.wordpress.org/Installing/Updating_WordPress_with_Subversion)
- [Changing File Permissions](http://codex.wordpress.org/Changing_File_Permissions)
- [Recursively delete .svn directories](http://www.anyexample.com/linux_bsd/bash/recursively_delete__svn_directories.xml)
- [Editing wp-config.php](http://codex.wordpress.org/Editing_wp-config.php)
- [WP Config](http://tumblr.jasontan.org/post/72133202/wp-config)
- [Giving WordPress its own Directory](http://codex.wordpress.org/Giving_WordPress_Its_Own_Directory)
