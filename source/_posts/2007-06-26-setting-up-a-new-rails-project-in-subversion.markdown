---
date: 2007-06-26 03:10:17
title: Setting up a new Rails project in Subversion
layout: post
wordpress_url: http://solutions.treypiepmeier.com/2007/06/setting-up-a-new-rails-project-in-subversion/
---
Create a folder to put all the junk you need to set things up.

	mkdir svn_setup
	cd svn_setup

Create the standard SVN folder structure.

	mkdir tags
	mkdir branches

Create a new Rails project and rename it to be the trunk folder.

	rails project_name
	mv project_name trunk

The reason to do this is so your database.yml file (among others) will have the right project name instead of `trunk_development`, etc.

A little housekeeping before putting the files into the repository.

	cd trunk
	rm -r tmp/*
	rm -r log/*
	mv config/database.yml config/database_example.yml

Put the files into the repository.

	cd ..
	svn import . svn_project_url -m "initial import of blank Rails project" --username whathaveyou

Checkout the files and tell Subversion to ignore some files.

	cd ..
	svn co svn_project_url/trunk project_name
	cd project_name
	cp config/database_example.yml config/database.yml
	svn propset svn:ignore database.yml config/
	svn propset svn:ignore "*" log/
	svn propset svn:ignore "*" tmp/

If you want, setup Rails with svn:externals to that it will be ready for you to lock it into a particular version for stability.

	svn propedit svn:externals vendor/

In the file that pops up, enter this (or enter whatever version you want to use--such as `http://dev.rubyonrails.org/svn/rails/trunk/` for edge):

	rails http://dev.rubyonrails.org/svn/rails/tags/rel_1-2-3/

Save then close the file.  

Check the changes back into the repository.

	svn ci -m "Ignore database.yml, log/, and temp/.  Set up Rails with svn:extnrnals"

Then update your checkout to get the Rails external to load.

	svn up

##Other things:

When you're done with everything you can delete the `svn_setup` folder.  I think I'm going to keep mine around for a slight head start on more projects.

Don't forget to use the -c option when you run `script/generate` to automatically add the files to Subversion.

	script/generate scaffold_resource angryfarmer name:string bales_of_hay:integer -c

When installing plugins, use the -x option to make it an svn:external

	script/plugin install -x robot_cow

## Source

- [Railscasts - Subversion on Rails](http://railscasts.com/episodes/36)
- [rails svn:externals for plugins and rails edge](http://snippets.dzone.com/posts/show/3251)
- [JTJ's comment below](#comment-4105)