---
date: 2009-03-09 20:40:23
title: Creating a Happy Git Environment on OS X Leopard
layout: post
wordpress_url: http://solutions.treypiepmeier.com/2009/03/a-happy-git-environment-on-osx-leopard/
---
- [Get the installer](http://code.google.com/p/git-osx-installer/)
- [Get GitX](https://github.com/brotherbard/gitx)

Configure things:

    git config --global user.name "Your Name"
    git config --global user.email "you@example.com"
    git config --global alias.co checkout
    git config --global apply.whitespace nowarn

Setup an SSH key

    ssh-keygen

Hit return a couple of times -- leave password blank if you want.

    cat ~/.ssh/id_rsa.pub | pbcopy

Paste that code into your [settings page](https://github.com/account) on your repository host(s).

Set up Global Git Config on your  [GitHub account page](https://github.com/account) (the same place you pasted your SSH key).  You'll type in some stuff that looks like this:

    git config --global github.user [your_username]
    git config --global github.token [your_token]

Get happy Git colors.  Paste the following into your `~/.gitconfig` file:

	[color]
		branch = auto
		diff = auto
		status = auto
	[color "branch"]
		current = yellow reverse
		local = yellow
		remote = green
	[color "diff"]
		meta = yellow bold
		frag = magenta bold
		old = red bold
		new = green bold
	[color "status"]
		added = yellow
		changed = green
		untracked = cyan

Create a `~/.gitexcludes` file and paste in this:

    .DS_Store

There, now you don't have to ignore that every time.

### Bash Fanciness

Add the following to your `~/.bash_profile` or `~/.bashrc`:

	source /usr/local/git/contrib/completion/git-completion.bash
	GIT_PS1_SHOWDIRTYSTATE=true
	export PS1='[\u@mbp \w$(__git_ps1)]\$ '

That will add tab auto-completion for Git branches, display the current branch on your prompt, and show a '*' after the branch name if there are unstaged changes in the repository, and a '+' if there are staged (but uncommitted) changes.  It will look something like this:

    [user@computer ~/Sites/example.com (master*)]$ 

### Bonus

If you want to have a different email address for a particular project (a personal project on your work computer, perhaps?), just run this command inside that project's folder:

	git config user.email "you@example.com"

It's the same command as before, this time just omitting the `--global`.

### Sources

- [PeepCode](http://peepcode.com/products/git)
- [Git Community Book](http://book.git-scm.com/2_setup_and_initialization.html)
