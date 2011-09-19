---
date: 2008-09-21 01:39:18
title: Using mod_wsgi with Django on Ubuntu
layout: post
wordpress_url: http://solutions.treypiepmeier.com/2008/09/using-mod_wsgi-with-django-on-ubuntu/
---
	sudo apt-get install libapache2-mod-wsgi

Virtual host configuration:

	<VirtualHost *:80>

		ServerAdmin you@example.com
		ServerName example.com
		DocumentRoot /home/you/public_html/example_com/public

		# Django settings
		WSGIScriptAlias / /home/you/public_html/example_com/wsgi_handler.py
		WSGIDaemonProcess example_com user=you group=you processes=1 threads=10
		WSGIProcessGroup example_com

		# Non-Django directories
		Alias /static /home/you/public_html/example_com/public/static/
		<Location "/static">
			SetHandler None
		</Location>

	</VirtualHost>

Put a file called `wsgi_handler.py` in your project folder:

	import os, sys

	sys.path.append(os.path.dirname(os.path.abspath(__file__)) + '/..')
	os.environ['DJANGO_SETTINGS_MODULE'] = 'example_com.settings'
 
	import django.core.handlers.wsgi
 
	application = django.core.handlers.wsgi.WSGIHandler()

### Sources

- [Django and mod_wsgi: A perfect match!](http://www.technobabble.dk/2008/aug/25/django-mod-wsgi-perfect-match/ "Django and mod_wsgi: A perfect match! | Technobabble - Christian Joergensen")
- [Setting up Django and mod_wsgi](http://ericholscher.com/blog/2008/jul/8/setting-django-and-mod_wsgi/ "Setting up Django and mod_wsgi | Surfing in Kansas")
