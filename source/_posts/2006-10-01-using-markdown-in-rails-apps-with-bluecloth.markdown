---
date: 2006-10-01 21:37:18
title: Using Markdown in Rails apps with BlueCloth
layout: post
wordpress_url: http://solutions.treypiepmeier.com/2006/10/using-markdown-in-rails-apps-with-bluecloth/
---
[RedCloth](http://whytheluckystiff.net/ruby/redcloth/) seems like a bad idea for doing [Mardown](http://daringfireball.net/projects/markdown/), since it wants to do [Textile](http://www.textism.com/tools/textile/) first then degrade to Markdown or some such nonsense.  Markdown = more better, IMO.

[Download BlueCloth gem](http://www.deveiate.org/projects/BlueCloth)

    sudo gem install ~/Desktop/BlueCloth-x.x.x.gem

###Syntax:

    <%= markdown(@item.description) %>