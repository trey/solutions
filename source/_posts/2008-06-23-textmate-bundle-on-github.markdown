---
date: 2008-06-23 17:18:31
title: Host a TextMate Bundle on GitHub
layout: post
wordpress_url: http://solutions.treypiepmeier.com/2008/06/textmate-bundle-on-github/
---
Create a repository on GitHub

Go into the Bundle Editor and drag your bundle to your desktop and `cd` into it in the terminal.  This is the key to the whole thing.  If you just go into the bundle where it lives in TextMate, you might not get everything it needs.  Dragging the file to the desktop makes it a nice, happy package ready to help other people.

Follow GitHub's instructions to set up and push to the remote repository.  Don't forget to `git add .` to get everything in there.

Delete your original bundle and then clone from GitHub like so:

	cd ~/"Library/Application Support/TextMate/Bundles/"
	git clone git://github.com/trey/trey-tmbundle.git "Trey.tmbundle"
	osascript -e 'tell app "TextMate" to reload bundles'

When you make changes to your Git-ified bundle in the Bundle Editor, you'll need to Reload Bundles for the changes to show up in your repository.  Then you'll need to `git add .` and commit / push as you would a normal repository.

### Source

* [Dr. Nic](http://github.com/drnic/github-tmbundle/)

