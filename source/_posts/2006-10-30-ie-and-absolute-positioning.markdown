---
date: 2006-10-30 02:34:48
title: IE and Absolute Positioning
layout: post
wordpress_url: http://solutions.treypiepmeier.com/2006/10/ie-and-absolute-positioning/
---
There are some seriously messed up things with absolute positioning in IE 6.  I struggled and struggled tonight trying to get a logo to sit in the top left part of the #wrapper div:

    #logo { position: absolute; }
    #wrapper { position: relative; }

The logo was just **not there**.  I ended up putting it in one of the main content columns, and it showed up in the right place (luckily, it also works in other browsers as well that way).

[I couldn't find much](http://www.google.com/search?q=absolute+positioning+ie&ie=utf-8&oe=utf-8&rls=org.mozilla:en-US:official&client=firefox-a), if anything, useful about this behavior.  Why do I always have some trouble with absolute positioning?  Why aren't more people blogging about this?  Absolute positioning is supposed to be so easy that it's considered cheating.