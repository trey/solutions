---
date: 2009-01-09 21:38:00
title: Django Model Class Style Guide
layout: post
wordpress_url: http://solutions.treypiepmeier.com/2009/01/django-model-class-style-guide/
---
1. Any constants and/or lists of choices
2. The full list of fields
3. The `Meta` class, if present
4. The `__unicode__()` method
5. The `save()` method, if it's being overridden
6. The `get_absolute_url()` method, if present
7. Any additional custom methods

### Sources

- [Practical Django Projects](http://readernaut.com/books/121/practical-django-projects/) p. 62 (pre-1.0 old admin stuff omitted)
- [Django Documentation](http://docs.djangoproject.com/en/dev/internals/contributing/#model-style)