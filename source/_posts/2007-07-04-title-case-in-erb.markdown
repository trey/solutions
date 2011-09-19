---
date: 2007-07-04 19:15:13
title: Title Case in ERb
layout: post
wordpress_url: http://solutions.treypiepmeier.com/2007/07/title-case-in-erb/
---
Use `.titleize` or `.titlecase`.  I'm using this in the `<title>` tag of my `application.rhtml`:

    <%= controller.action_name.titleize %>

### Source

- [Rails API](http://api.rubyonrails.org/classes/ActiveSupport/CoreExtensions/String/Inflections.html#M000425)
