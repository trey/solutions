---
date: 2010-01-10 09:46:50
title: Create Your Own Local Copy of the Django Documentation
layout: post
wordpress_url: http://solutions.treypiepmeier.com/2010/01/local-django-documentation/
---
	sudo easy_install Sphinx
	
Inside your local SVN checkout of Django:

	cd docs
	make html

Now you'll have a beautiful local copy of the documentation to browse for those rare moments when you're away from the internet (perhaps you're [in a fort](http://djangocon.blip.tv/file/3040084/)?). Just point your browser to:

	file:///path/to/your/django/docs/_build/html/index.html

### Source

- [eddymulyono](http://eddymulyono.livejournal.com/74322.html)