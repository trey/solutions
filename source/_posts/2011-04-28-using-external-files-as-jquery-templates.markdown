---
date: 2011-04-28 19:45:15
title: Using External Files as jQuery Templates
categories: [JavaScript, jQuery]
layout: post
wordpress_url: http://solutions.treypiepmeier.com/2011/04/using-external-files-as-jquery-templates/
---
[Previously&hellip;](/2010/10/25/jquery-templates/)

If you want to keep your templates in external files, you can load the template in like so:

```javascript
$.get('/js/templates/filename.html', function(template) {
	$.tmpl(template, data).appendTo('#whatever');
});
```

A couple of benefits of this method:

- Organizing your templates into their own files is tidy.
- Your syntax highlighter will be happier, since you're not writing HTML between two `<script>` tags.

### Source

- [Dave Ward](http://encosia.com/2010/10/05/using-external-templates-with-jquery-templates/)