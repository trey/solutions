---
date: 2009-01-21 17:08:15
title: Display Children of One-To-Many or Many-To-Many Relationships in your Django Templates
layout: post
wordpress_url: http://solutions.treypiepmeier.com/2009/01/one-to-many-or-many-to-many-relationships-in-django-templates/
---
For items you've defined in the parent model, such as this:

	class Project(models.Model):
		tasks = models.ManyToManyField(Task, blank=True)

You use `parent.children.all`, like so:

	{% for task in project.tasks.all %}
		<li>{{ task.title }}</li>
	{% endfor %}

For items defined outside of the parent model with a foreign key pointing back to the parent model, such as this:

	class Picture(models.Model):
		project = models.ForeignKey(Project)

You use `parent.children_set.all`, like so:

	{% for picture in project.picture_set.all %}
		<img src="{{ picture.image }}" alt="{{ project.title }}">
	{% endfor %}

### Sources

- [Django documentation](http://docs.djangoproject.com/en/dev/topics/db/models/)
- [Django Gotchas](http://playgroundblues.com/posts/2006/jun/30/django-gotchas/)

