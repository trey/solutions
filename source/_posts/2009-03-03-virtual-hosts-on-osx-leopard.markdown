---
date: 2009-03-03 21:24:47
title: The Absolute Least You Need to do to use Virtual Hosts on OS X Leopard
layout: post
wordpress_url: http://solutions.treypiepmeier.com/2009/03/virtual-hosts-on-osx-leopard/
---
Enable `Web Sharing` in System Preferences > Sharing.

Edit these files:

- `/etc/apache2/httpd.conf`
- `/etc/hosts`
- `/etc/apache2/users/your-username.conf`

(I keep these files in a TextMate project so I can get at them quickly and don't have to remember which files I need.)

In `httpd.conf`, uncomment this line:

    LoadModule php5_module        libexec/apache2/libphp5.so

In `hosts`, add your local sites in the format:

    127.0.0.1	your-site-name.dev

In `/etc/apache2/users/your-username.conf`, add this line to the very top of the file:

    NameVirtualHost *:80

Change `None` to `All` in this line (to allow for things like `mod_rewrite`):

    AllowOverride All

Add `FollowSymlinks` to this line:

    Options Indexes MultiViews FollowSymlinks

Add new sites in the same file in this format:

	<VirtualHost *:80>
	   ServerName your-site-name.dev
	   DocumentRoot "/Users/your-username/Sites/your-site-name/"
	</VirtualHost>

Any time you make changes to any of these files, you'll need to run this command:

    sudo apachectl graceful

Check out [this script](http://gist.github.com/292032) for an easy way to add new sites (and feel free to fork it and adapt it to your uses).
