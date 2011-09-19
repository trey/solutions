---
date: 2008-02-25 07:47:33
title: Installing Git on OS X Leopard
layout: post
wordpress_url: http://solutions.treypiepmeier.com/2008/02/installing-git-on-os-x-leopard/
---
- [Download the installer](http://code.google.com/p/git-osx-installer/)
- [Go create your happy environment](/2009/03/09/a-happy-git-environment-on-osx-leopard/)

### Bonus: TextMate Integration

To use TextMate to edit your commit messages, put the following in your `~/.bashrc` or `~/.bash_profile` (or other [dot goodness](http://github.com/trey/dotfiles)):

    export GIT_EDITOR="mate -w"

Since Git is isn't installed in `/usr/bin/git` where TextMate expects it, make a symlink:

    sudo ln -s `which git` /usr/bin/git


