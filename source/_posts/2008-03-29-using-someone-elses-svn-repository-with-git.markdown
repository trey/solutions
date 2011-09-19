---
date: 2008-03-29 15:23:55
title: Using Someone Else's SVN Repository with Git
layout: post
wordpress_url: http://solutions.treypiepmeier.com/2008/03/using-someone-elses-svn-repository-with-git/
---
If you have a repository URL that looks like this:

	http://code.yourmom.com/project/trunk/

Issue this command (note that you leave off `trunk/`):

	git svn clone -s http://code.yourmom.com/project/ project

After it's done, see how big it is:

	du -hs project

And you'll see something like this:

	20M project/

If it's particularly big, go into the folder and garbage collect:

	cd project
	git gc

From within the project folder, set your local repository to the trunk (it's set to whatever branch had the last commit otherwise):

	git reset --hard trunk

Create your own branch and get to work:

	git co -b treys_changes

When you want to pull in the changes from the original author to stay up to date:

	git svn rebase

If you've cloned this repo (after posting it to [GitHub](http://github.com) or elsewhere) and want to use it on another computer, you'll have to use do more step in order to track the original SVN repo again:

	git update-ref refs/remotes/trunk origin/master
	git svn init -T trunk http://code.yourmom.com/project/

### Sources

- Brian Rosner's [Using git with Django Screencast](http://oebfare.com/blog/2008/jan/23/using-git-django-screencast/)
- Pieter on [#github](irc://irc.freenode.net/github)
- [WebKit wiki](http://trac.webkit.org/projects/webkit/wiki/UsingGitWithWebKit#Checkout) (via Pieter)
