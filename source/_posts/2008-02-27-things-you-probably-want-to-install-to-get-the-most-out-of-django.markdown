---
date: 2008-02-27 03:39:10
title: Things you probably want to install to get the most out of Django
layout: post
wordpress_url: http://solutions.treypiepmeier.com/2008/02/things-you-probably-want-to-install-to-get-the-most-out-of-django/
---
## libjpeg (for PIL)

	curl -O http://www.ijg.org/files/jpegsrc.v6b.tar.gz
	tar zxvf jpegsrc.v6b.tar.gz
	cd jpeg-6b/
	./configure
	make
	sudo make install-lib

## [Python Image Library (PIL)](http://www.pythonware.com/products/pil/)

	curl -O http://effbot.org/media/downloads/Imaging-1.1.6.tar.gz
	tar zxvf Imaging-1.1.6.tar.gz 
	cd Imaging-1.1.6
	sudo python setup.py install

## [Python Markdown library](http://www.freewisdom.org/projects/python-markdown)

	curl -O http://pypi.python.org/packages/source/M/Markdown/markdown-1.7.tar.gz
	tar zxvf markdown-1.7.tar.gz
	cd markdown-1.7
	sudo python setup.py install

[See also.](/2006/09/20/getting-markdown-to-work-with-django/)

## [Docutils](http://docutils.sourceforge.net/)

This makes Django's built-in admin documentation work.

	curl -O http://docutils.sourceforge.net/docutils-snapshot.tgz
	tar zxvf docutils-snapshot.tgz
	cd docutils
	sudo python setup.py install

### Sources

- [paul.annesley.cc](http://paul.annesley.cc/articles/2007/11/19/django-and-python-imaging-library-pil-on-leopard)