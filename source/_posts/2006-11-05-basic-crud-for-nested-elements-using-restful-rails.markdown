---
date: 2006-11-05 08:53:53
title: Basic CRUD for Nested Elements using RESTful Rails
layout: post
wordpress_url: http://solutions.treypiepmeier.com/2006/11/basic-crud-for-nested-elements-using-restful-rails/
---
Continuing from [where we left off](http://solutions.treypiepmeier.com/2006/10/11/basic-crud-using-rest-in-rails-incomplete/)...

(This all assumes you've set your app up using `script/generate scaffold_resource` with all the bells and whistles of spelling out your table columns in the command line.)

Make sure you've got your model relationships set up right:

	# app/models/manufacturer.rb
	has_many :appliances

	# app/models/appliance.rb
	belongs_to :manufacturer
	
Set up your nested routes:

	map.resources :manufacturers do |manufacturers|
		manufacturers.resources :appliances
	end

In the controller for the dependent item, at the top of the file:

	# app/controllers/appliances_controller.rb
	before_filter :load_manufacturers
	
Then at the bottom of the same file:

	private
	
	def load_manufacturers
		@manufacturer = manufacturer.find(params[:manufacturer_id])
	end

Then back at the top of that file, for the `index` action:

	@appliances = @manufacturer.appliances.find(:all)

Now for the views.  To get started: in `app/views/appliances/index.rhtml` you should make sure that calls to `appliance_path` get the manufacturer id passed to them:

    <%= link_to 'Show', appliance_path(@manufacturer, appliance) %>

In `edit.rhtml` and `new.rhtml` (or your `_form.rhtml` partial), you can remove the part of the form that lets you specify what manufacturer you want within the new/edit appliance form.  You'll get that from the `params[:manufacturer_id]` anyway.  In the edit template, you'll need to change the form a little bit for it to work:

	# app/views/appliances/edit.rhtml

	<% form_for(:appliance, :url => appliance_path(@manufacturer, @appliance), :html => { :method => :put }) do |f| %>

Notice we have to specifically specify the `@manufacturer`.  Now back to the appliances controller:

	def create
		@appliance = appliance.new(params[:appliance])
		@appliance.manufacturer_id = params[:manufacturer_id]

	    respond_to do |format|
	      if @appliance.save
	        flash[:notice] = 'Appliance was successfully created.'

	        format.html { redirect_to appliance_url(@appliance.manufacturer_id, @appliance) }
		...

It's not smart enough to know that it needs the `manufacturer_id` param that's just sitting there in the URL waiting to be used for something.  Just about anywhere you need the `appliance_url()`, you have to specify the `manufacturer_id`.  Whether it's a param, or if it's already sitting in the item you're using:

	# app/controllers/appliances_controller.rb
	def update
		...
		if @appliance.update_attributes(params[:appliance])
	      format.html { redirect_to appliance_url(@appliance.manufacturer_id, @appliance) }
    	...

Hope that helps.  It's simple, right? ;)

Thanks again to [PeepCode](http://peepcode.com/articles/2006/10/08/restful-rails)!