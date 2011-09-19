---
date: 2007-05-06 01:26:40
title: Restore MySQL databases from a hard drive backup
layout: post
wordpress_url: http://solutions.treypiepmeier.com/2007/05/restore-mysql-databases-from-a-hard-drive-backup/
---
Drag everything from `/usr/local/mysql/data` into the same location on the new installation, overwriting whatever is there.  You may have to `chown` the folder from `mysql` to your user name, just don't forget to `chown` it back or it won't start up again.

No dumps needed.

I hope this will show up in a [Google search for "`restore mysql databases "without dump"`"](http://www.google.com/search?hl=en&safe=off&client=firefox-a&rls=org.mozilla%3Aen-US%3Aofficial&hs=fAp&q=restore+mysql+databases+%22without+dump%22&btnG=Search)