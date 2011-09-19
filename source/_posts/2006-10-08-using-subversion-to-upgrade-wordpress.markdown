---
date: 2006-10-08 20:05:15
title: Using Subversion to upgrade WordPress
layout: post
wordpress_url: http://solutions.treypiepmeier.com/2006/10/using-subversion-to-upgrade-wordpress/
---
* [Use svn:externals to install WordPress plugins](http://fucoder.com/2006/04/svnexternal-wordpress-plugins/)
* [How to use SVN to update WordPress](http://sethkinast.com/blog/archive/2005/05/31/svn-wordpress/)
* [Subversioning WordPress Upgrades](http://photomatt.net/2005/05/19/subversioning-wordpress-upgrades/)

**Update (November 1, 2006):** It really works.  I've got all 3 of my blogs ([one](http://syntheticrabbit.com/blog/) [two](http://treypiepmeier.com/) [three](http://solutions.treypiepmeier.com/)) now set up on SVN.  The next step will to be when I add my customized themes to Subversion so all I ever have to do is go to the command line to do anything.  No (s)FTP or anything.  I imagine this will make switching servers really easy now.

**Update (January 23, 2007):** To upgrade to WordPress 2.1:

1. Disable all plugins (take a screenshot first)
2. Run this command:
    <pre><code>svn switch http://svn.automattic.com/wordpress/branches/2.1/</code></pre>
3. Go to your admin screen and update the database when prompted.
4. Enable your plugins again.

**Update (May 22, 2007):** Just upgraded to version 2.2