---
date: 2007-05-06 01:39:19
title: Restoring keychain passwords (including Transmit) from a hard drive backup
layout: post
wordpress_url: http://solutions.treypiepmeier.com/2007/05/restoring-keychain-passwords-including-transmit-from-a-hard-drive-backup/
---
This worked for me:

* Rename the file `~/Library/Keychains/login.keychain` (to keep it safe just in case)
* Drag your backup copy of `login.keychain` to the same location
* Make sure your admin account on your new system (or install of OS X) has the same password as the old one, or ([according to JTJ](http://twitter.com/postpostmodern/statuses/51315242)) it won't automatically open it when you log in.

**Source:** Originally [tweeted](http://twitter.com/trey/statuses/51304612).