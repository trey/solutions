---
date: 2010-11-13 23:06:53
title: Determine if a jQuery click event was triggered by a user or a script calling the .click() method
categories: [jQuery, JavaScript]
layout: post
wordpress_url: http://solutions.treypiepmeier.com/2010/11/determine-if-a-jquery-click-event-was-triggered-by-a-user-or-a-script-calling-the-click-method/
---
    $('.button').click(function(e) {
        if (e.originalEvent) {
            // user click
        } else {
            // .click()
        };  
    });

### Source
- [chiel's comment on the jQuery API](http://api.jquery.com/click/#comment-49384681)