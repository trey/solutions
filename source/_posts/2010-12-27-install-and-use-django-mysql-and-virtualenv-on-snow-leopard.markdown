---
date: 2010-12-27 18:30:51
title: Install and Use Django, MySQL, and VirtualEnv on Snow Leopard
layout: post
wordpress_url: http://solutions.treypiepmeier.com/2010/12/install-and-use-django-mysql-and-virtualenv-on-snow-leopard/
---
### Django

	mkdir -p ~/src
	svn co http://code.djangoproject.com/svn/django/trunk/ ~/src/django
	ln -s ~/src/django/django `python -c "from distutils.sysconfig import get_python_lib; print get_python_lib()"`/django
	ln -s ~/src/django/django/bin/django-admin.py ~/bin/django-admin.py

### PIP, mysql-python, virtualenv, virtualenvwrapper, Mercurial

Download and install the [MySQL package installer](http://dev.mysql.com/downloads/mysql/), then:

	easy_install pip
	pip install http://downloads.sourceforge.net/project/mysql-python/mysql-python-test/1.2.3c1/MySQL-python-1.2.3c1.tar.gz?use_mirror=cdnetworks-us-2
	pip install virtualenv
	pip install virtualenvwrapper
	pip install mercurial
	
(Note: we're installing Mercurial because a lot of PIP packages require it)

In [`~/bin/dotfiles/bash/env`](https://github.com/trey/dotfiles/blob/master/bash/env)

	export WORKON_HOME=$HOME/.virtualenvs
	source /usr/local/bin/virtualenvwrapper.sh
	. ~/src/django/extras/django_bash_completion

Then

	mkdir -p ~/.virtualenvs
	source ~/.bashrc

Install libjpeg from scratch (for PIL):

	cd ~/src
	curl -O http://www.ijg.org/files/jpegsrc.v8a.tar.gz
	tar zxvf jpegsrc.v8a.tar.gz
	cd jpeg-8a
	./configure
	make
	make install

### Setup a project

	cd [path/to/your/project/]
	mkvirtualenv [projectname]
	add2virtualenv .
	echo 'cd [path/to/your/project/]' >> $WORKON_HOME/postactivate

Put requirements for your project into a requirements.txt [like so](http://gist.github.com/322455):

A package on its own line:

	docutils==0.6

Repo noted like so:

	-e git://github.com/mintchaos/typogrify.git#egg=Typogrify

### To install things in your requirements file

	pip install -r requirements.txt

### Starting and Stopping VirtualEnvs

Start:

	workon [project]

Stop:

	deactivate

### Sources

- [PyPi](http://pypi.python.org/pypi/virtualenv)
- [VirtualEnvWrapper](http://www.doughellmann.com/projects/virtualenvwrapper/)
- [VirtualEnvWrapper docs](http://www.doughellmann.com/docs/virtualenvwrapper/)
- [epicserv's Gist](https://gist.github.com/311159)
- [mathematism](http://mathematism.com/2009/07/30/presentation-pip-and-virtualenv/)
- [b-list](http://www.b-list.org/weblog/2008/dec/15/pip/)
