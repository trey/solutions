---
date: 2009-11-09 22:55:42
title: How to Log Something
layout: post
wordpress_url: http://solutions.treypiepmeier.com/2009/11/how-to-log-something/
---
### With The Django Debug Toolbar

Somewhere in your Python code (not a template):

    import logging
    logging.debug(something_you_want_to_log)

### With Firebug

Somewhere in your JavaScript or the Firebug Console:

    console.log(something_you_want_to_log);

That was easy.

### Sources

- [Alex](http://eatshitnerds.com/)
- [Firebug Console API](http://getfirebug.com/console.html)
