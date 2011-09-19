---
date: 2009-03-09 01:19:50
title: Setting up a Tracking Branch in Git
layout: post
wordpress_url: http://solutions.treypiepmeier.com/2009/03/setting-up-a-tracking-branch-in-git/
---
If you have an open source repository, or you're sharing code with a team, you'll probably want to pull in changes from other people and merge them into your code.  Here's how to do it.

    git remote add [persons_name] [url_to_repository]
    git fetch [persons_name]
    git branch --track [persons_name] [persons_name]/master
    git merge [persons_name]
    git push

This sets up a local branch that's only job is to track the other person's repository.  Any time you want to pull in their changes and merge them with yours:

    git co [persons_name]
    git pull
    git co master
    git merge [persons_name]

### Sources

- [PeepCode](http://peepcode.com/products/git)
- [GitCasts](http://www.gitcasts.com/posts/distributed-workflow)