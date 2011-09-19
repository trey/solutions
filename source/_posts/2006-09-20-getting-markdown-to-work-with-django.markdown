---
date: 2006-09-20 07:35:30
title: Getting Markdown to work with Django
layout: post
wordpress_url: http://solutions.treypiepmeier.com/2006/09/getting-markdown-to-work-with-django/
---
In your view template put:

	{% load markup %}

In your settings.py in the INSTALLED_APPS section, put:

	'django.contrib.markup',

###Install the Markdown library:

[Download](http://www.freewisdom.org/projects/python-markdown)

###Install on OS X:

Download markdown.py and setup.py and run:

	python setup.py install

This is what happened on my system:

	running install
	running build
	running build_py
	creating build
	creating build/lib
	copying markdown.py -> build/lib
	running install_lib
	copying build/lib/markdown.py -> /System/Library/Frameworks/Python.framework/Versions/2.3/lib/python2.3/site-packages
	byte-compiling /System/Library/Frameworks/Python.framework/Versions/2.3/lib/python2.3/site-packages/markdown.py to markdown.pyc

I wonder if that was the wrong way to do that.  It looks like it modified my system version of Python, which means if the system updates it, it will be overwritten, right?

###Install on DreamHost

[Croft tells it like it is:](http://www2.jeffcroft.com/2006/may/11/django-dreamhost/)

> Basically, you just want to put the markdown.py file anywhere in your Python path. The simplest way is to just drop markdown.py in your django\_projects directory. A slighty more complicated, but cleaner way (and actually the way I did it) is to create another directory for Python modules like this. I created a directory at the root of my Dreamhost account called "pylib". You then need to add this directory to your python path by adjusting .bashrc and django.fcgi accordingly. If that makes sense, go for it. If not, just drop markdown.py in your django\_projects -- that'll work fine.