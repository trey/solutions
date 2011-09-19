---
date: 2009-09-15 19:05:39
title: Remove a Git Submodule
layout: post
wordpress_url: http://solutions.treypiepmeier.com/2009/09/remove-a-git-submodule/
---
1. Delete the relevant line from the `.gitmodules` file. 
2. Delete the relevant section from `.git/config`. 
3. Run `git rm --cached path/to/submodule` (no trailing slash). 
4. Commit and delete the now untracked submodule files.

### Source

- Chat conversation with [JTJ](http://postpostmodern.com).