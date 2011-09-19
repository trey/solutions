---
date: 2009-07-17 16:32:55
title: My Git Workflow
layout: post
wordpress_url: http://solutions.treypiepmeier.com/2009/07/my-git-workflow/
---
### Local Branches

There are some common hickups I see in the day-to-day use of Git that can be fairly easily remedied by the liberal use of local branches.

When I start any new work (or at the very least before I commit my work), I create a new local branch named for the feature on which I'm working.

	git co -b feature-branch

I might work on that feature for a few minutes, or it could take several days.  In the meantime, I can keep up with what my coworkers are doing with the same repository without it ever conflicting with what I'm doing.

When I want to pull in other people's changes, I simply go to my local tracking branch and pull in the changes.

	git co my-local-tracking-branch
	git pull

In order to keep my new feature branch up-to-date with the rest of the repository, I simply rebase against it periodically.

	git co feature-branch
	git rebase my-local-tracking-branch

This is a potentially dangerous way of "merging" in changes, but as long as you never push your feature branch anywhere (until you **do** merge it into the tracking branch), it's perfectly safe.  The reason it can be dangerous is that it does a bit of history re-writing.  A rebase takes all your feature branch changes and rewrites them as if they took place after all the changes from everyone else.  I think this is good for a couple of reasons:

1. Your commits for your feature branch will show up at the top of `git log`.  As soon as you push your changes to the shared branch, you'll see all your stuff first (as opposed to interspersed throughout the log depending on the time you made the commits).
2. You can pretty much stop seeing commit messages that are automatically generated "`Merge branch 'whatever' into 'whatever-else'`," since you rebased instead of merged.

When I've finished working on the feature branch and rebased in everyone else's changes a last time, I'll merge it into the tracking branch.

	git co my-local-tracking-branch
	git merge feature-branch

Since the feature branch has everything in that's in the tracking branch, it doesn't create a new merge commit.  Everything's just happy.  Push your changes and get rolling on the next feature.

### Amend

In order to really keep my commits clean, I try to limit myself to a single commit for a feature (or ticket).  I continue to commit obsessively (as is my nature), but all that ever shows up in the public repository is a single commit.  That's because I use:

	git commit --amend

As with rebasing, you should only ever do this on commits that haven't been pushed anywhere.  As long as you're doing this on your feature branch, you'll be safe.

Doing this is even easier if you use [GitX](http://gitx.frim.nl/): just click the "Amend" checkbox.

By using `amend`, you can keep adding changes to the same commit, and revise the commit message as you do more and more things.
