---
date: 2007-01-01 19:14:33
title: has_many :through
layout: post
wordpress_url: http://solutions.treypiepmeier.com/2007/01/has_many-through/
---
> Has Many associations can be configured with the :through option to use an explicit join model to retrieve the data. This operates similarly to a has\_and_belongs\_to\_many association. **The advantage is that you're able to add validations, callbacks, and extra attributes on the join model.** Consider the following schema:

	class Author < ActiveRecord::Base
	  has_many :authorships
	  has_many :books, :through => :authorships
	end

	class Authorship < ActiveRecord::Base
	  belongs_to :author
	  belongs_to :book
	end

	@author = Author.find :first
	@author.authorships.collect { |a| a.book } # selects all books that the author's authorships belong to.
	@author.books                              # selects all books by using the Authorship join model

###Sources

* [Association Join Models](http://rails.rubyonrails.com/classes/ActiveRecord/Associations/ClassMethods.html) (search for "Association Join Models")
* [Through Associations](http://wiki.rubyonrails.com/rails/pages/ThroughAssociations)