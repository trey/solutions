---
date: 2010-11-03 16:49:08
title: Optional Parameters in JavaScript Functions
layout: post
wordpress_url: http://solutions.treypiepmeier.com/2010/11/optional-parameters-in-javascript-functions/
---

``` javascript Set it up
adjustDisplay: function(smooth){
    if (smooth === undefined) { smooth = false };
    ...
    if (smooth) {
        $('#content').animate({height: '500px'}, 200);
    } else {
        $('#content').css('height', '500px');
    };
},
...
```

``` javascript Call it
app.adjustDisplay('smooth');
```