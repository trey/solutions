---
date: 2010-02-22 22:02:38
title: Using Dropbox to Share Git Repositories
layout: post
wordpress_url: http://solutions.treypiepmeier.com/2010/02/using-dropbox-to-share-git-repositories/
---
First, create a Git subfolder inside your Dropbox folder. Then you can share the individual projects inside that folder with whomever you want (or just use it for instant offsite backups).

From inside a Git project:

    git clone --bare . ~/Dropbox/Git/gitproject.git
    git remote add dropbox ~/Dropbox/Git/gitproject.git

When you're ready to push:

    git push dropbox master

### Your Collaborator's View

Your collaborator would work on the project like so (inside the folder where they want their project to live):

    git clone ~/Dropbox/Git/gitproject.git

If they want to have a `dropbox` remote instead of the default `origin`:

    git remote add dropbox ~/Dropbox/Git/gitproject.git

They would then push the same way:

    git push dropbox master

To get the other person's changes, it's the standard deal:

    git pull dropbox master

### Source
- [Cocoa Is My Girlfriend](http://www.cimgf.com/2008/06/03/version-control-makes-you-a-better-programmer/)