---
date: 2009-05-14 15:49:44
title: Dealing with the IE 7 (and 8) Transparency Bug with jQuery
layout: post
wordpress_url: http://solutions.treypiepmeier.com/2009/05/dealing-with-the-ie-7-transparency-bug-with-jquery/
---
I found out this morning that you can't use jQuery's `fadeIn` or `fadeOut` in IE 7 or 8 on elements that have transparent pngs as backgrounds because the animation will make the transparency turn black.  It's a good thing browser detection is built into jQuery(!).

    if ($.browser.msie && $.browser.version < 9 ) {
        $('#whatever').hide();
    } else {
        $('#whatever').fadeOut();
    }

Excellent.

### Sources

* [jQuery Development Google Group](http://groups.google.com/group/jquery-dev/msg/f3bc9685ccb40e70)
* [8 awesome JQuery tips and tricks](http://www.catswhocode.com/blog/8-awesome-jquery-tips-and-tricks)
