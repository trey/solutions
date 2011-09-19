---
date: 2008-12-26 08:56:35
title: Serve Django Projects with Phusion Passenger
layout: post
wordpress_url: http://solutions.treypiepmeier.com/2008/12/serve-django-projects-with-phusion-passenger/
---
This is almost too easy.  The only thing you need to do on top of what needs to be done for a Rails project is to add the following to a file called `passenger_wsgi.py` in the root folder of your project.

    import os, sys
    sys.path.append('/path/to/your/DjangoProjects')
    os.environ['DJANGO_SETTINGS_MODULE'] = 'example_com.settings'

    import django.core.handlers.wsgi

    application = django.core.handlers.wsgi.WSGIHandler()

Then you create a basic virtual host configuration like you would for a PHP site:

	<VirtualHost *:80>
	   ServerName example.com
	   DocumentRoot "/path/to/example_com/public/"
	</VirtualHost>

I have yet to try this on a production server, but it works perfectly on my local machine.  It even works with the [Passenger preference pane](http://webslinger.tumblr.com/post/62866959/passenger)!

### Sources

- [kwe on GitHub](http://github.com/kwe/passenger-django-wsgi-example/)
- I was inspired to finally try this by [topfunky's comment](http://webslinger.tumblr.com/post/65229983/passenger-on-dreamhost).