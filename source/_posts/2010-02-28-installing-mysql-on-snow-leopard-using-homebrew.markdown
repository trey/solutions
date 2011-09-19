---
date: 2010-02-28 18:42:59
title: Installing MySQL on Snow Leopard using Homebrew
layout: post
wordpress_url: http://solutions.treypiepmeier.com/2010/02/installing-mysql-on-snow-leopard-using-homebrew/
---
If you already have a [`/usr/local`][usrlocal] folder and it's not owned by your user:

	sudo chown -R `whoami` /usr/local

Install [Homebrew][homebrew]:

	cd /usr/local
	git init
	git remote add origin git://github.com/mxcl/homebrew.git
	git pull origin master

This is kind of odd--you install Homebrew right into the base of your `/usr/local` folder.  It nicely ignores other folders that already exists there.  Just do it.

Install MySQL:

	brew install mysql

Yeah, it's really that easy.  This will take a while.

Now warm it up:

	mysql_install_db

And make sure it automatically starts again on login:

	launchctl load -w /usr/local/Cellar/mysql/5.1.43/com.mysql.mysqld.plist

[usrlocal]: http://hivelogic.com/articles/using_usr_local
[homebrew]: http://github.com/mxcl/homebrew
