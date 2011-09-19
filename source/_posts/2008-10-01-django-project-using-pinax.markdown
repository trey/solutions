---
date: 2008-10-01 00:25:15
title: Setting up a New Django Project Using Pinax
layout: post
wordpress_url: http://solutions.treypiepmeier.com/2008/10/django-project-using-pinax/
---
	svn co http://django-hotclub.googlecode.com/svn/trunk/ [name_of_site]
	cd [name_of_site]/projects
	cp -R complete_project [name_of_project]
	cd [name_of_project]
	rm -rf `find . -type d -name .svn`
	echo "ROOT_URLCONF = '[name_of_project].urls'" > localsettings.py

Now import the contents of `[name_of_site]/projects/[name_of_project]/` into your choice of source code management systems and start developing your Pinax-based project.  Put all new apps, templates, and media inside that folder.  You can base your templates and media on the ones you copied when you duplicated the `complete_project/` folder, or wipe them out and start from scratch.

When you're ready to deploy, check [here](http://pinaxproject.com/docs/deployment.html "Deployment &mdash; Pinax v0.1dev documentation") and [here](http://www.20seven.org/journal/2008/09/pinax-setup-and-deploy.html "Pinax Setup and Deployment - journal").

### Sources

- [Customization &mdash; Pinax v0.1dev documentation](http://pinaxproject.com/docs/customization.html)
- [Noob question - django-hotclub | Google Groups](http://groups.google.com/group/django-hotclub/browse_thread/thread/1cb2bc202a29f803)

