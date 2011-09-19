---
date: 2008-03-06 04:08:05
title: Django Template System Basics
layout: post
wordpress_url: http://solutions.treypiepmeier.com/2008/03/django-template-system-basics/
---
### The long way

1. Load a template
2. Fill a `Context`
3. Return a `HttpResponse` object

Like so:

	from django.template import Template, Context
	from django.http import HttpResponse
	...
	t = get_template('current_datetime.html')
	html = t.render(Context({'current_date': now}))
	return HttpResponse(html)

### The short way: `render_to_response`

Like so:

	from django.shortcuts import render_to_response
	...
	return render_to_response('current_datetime.html', {'current_date': now})

### Source:

- [The Django Book](http://djangobook.com/en/1.0/chapter04/) (pages 51, 52 of the print edition)