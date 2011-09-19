---
date: 2008-09-29 03:14:07
title: Use Django Fixtures to Automatically Load Data when You Install an App
layout: post
wordpress_url: http://solutions.treypiepmeier.com/2008/09/use-django-fixtures-to-automatically-load-data-when-you-install-an-app/
---
First, load some data via the admin that should always be there when someone installs the app.

Next, dump that data out into JSON format into a fixture:

	./manage.py dumpdata [app_name] > [app_name]/fixtures/initial_data.json

Now whenever someone installs the app and runs `syncdb`, they'll get that initial data loaded into their database.


### Sources

- [Providing initial data for models](http://docs.djangoproject.com/en/dev/howto/initial-data/#providing-initial-data-with-fixtures "Django | Providing initial data for models | Django Documentation")
- [django-admin.py and manage.py](http://docs.djangoproject.com/en/dev/ref/django-admin/#dumpdata "Django | django-admin.py and manage.py | Django Documentation")
