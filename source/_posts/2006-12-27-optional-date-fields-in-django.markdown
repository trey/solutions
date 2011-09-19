---
date: 2006-12-27 09:02:39
title: Optional Date Fields in Django
layout: post
wordpress_url: http://solutions.treypiepmeier.com/2006/12/optional-date-fields-in-django/
---
Adding `blank=True` on any field in your `models.py` file will keep the admin interface from requiring that field.  That's all you need to do if it's a string field.  If it's an integer, boolean, or a date; you need to add `null=True` to the field as well.

    date = models.DateField(blank=True, null=True)

###Source
[Django model reference](http://www.djangoproject.com/documentation/model_api/#null)

###See also
[When to use and when not to use NOT NULL in MySQL / Rails Migrations](http://solutions.treypiepmeier.com/2006/09/22/when-to-use-and-when-not-to-use-not-null-in-mysql/)