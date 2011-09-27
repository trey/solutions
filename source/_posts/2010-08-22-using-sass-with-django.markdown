---
date: 2010-08-22 19:00:38
title: Using Sass with Django
categories: [Sass, Django]
layout: post
wordpress_url: http://solutions.treypiepmeier.com/2010/08/using-sass-with-django/
---
Install [django-css](http://github.com/dziegler/django-css/).

Install [Sass](http://sass-lang.com/).
	
	sudo gem install haml

Add to `settings.py`:

``` python settings.py
INSTALLED_APPS = (
	...
	'compressor',
	...
)

...

COMPILER_FORMATS = {
    '.sass': {
        'binary_path':'sass',
        'arguments': '*.sass *.css'
    },
    '.scss': {
        'binary_path':'sass',
        'arguments': '*.scss *.css'
    }
}
```

Add to a template that you want to load a Sass file:
	
``` django
{ % load compress % }

...

{ % compress css % }
<link rel="stylesheet" href="{{ MEDIA_URL }}css/base.scss" media="screen">
{ % endcompress % }
```

Dealssss with [caching](http://docs.djangoproject.com/en/dev/topics/cache/) when you deploy.

Perhaps pip install `python-memcached` then put something like this in 
`settings.py`

``` python
CACHE_BACKEND = 'memcached://127.0.0.1:11211/'
```

Write some nice Sass.

``` sass Your snazzy Sass file
$orange: #EE8529;

ul {
	font-size: 26px;
	li {
		color: $orange;
	}
}
```
