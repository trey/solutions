---
date: 2011-01-07 16:25:18
title: Temporarily ignore a file in Git
layout: post
wordpress_url: http://solutions.treypiepmeier.com/2011/01/temporarily-ignore-a-file-in-git/
category: Git
---
Sometimes you want to temporarily ignore a file in a Git repository without throwing it out entirely by putting it in `.gitignore`. Here's how to do it:

    git update-index --assume-unchanged [filename]

To start tracking changes again:

    git update-index --no-assume-unchanged [filename]

### Source

- [Git Ready](http://gitready.com/intermediate/2009/02/18/temporarily-ignoring-files.html)
