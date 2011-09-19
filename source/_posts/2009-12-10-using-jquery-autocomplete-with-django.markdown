---
date: 2009-12-10 23:08:22
title: Using the jQuery Autocomplete Plugin with Django
layout: post
wordpress_url: http://solutions.treypiepmeier.com/2009/12/using-jquery-autocomplete-with-django/
---
Here's another look into the development of [ComicBinder](http://comicbinder.com).

There's already [a good tutorial on how to use an autocomplete plugin with Django][tut], but I wanted to use [this much snazzier plugin][jqac].

### The Process

Load both `jquery.autocomplete.min.js` and `jquery.autocomplete.css` in your page.

In your form object, create a `CharField` to hold your autocomplete. Something like:

```python
    title = forms.CharField(label='', widget=forms.TextInput(attrs={'placeholder': 'The name of a comic'}))
```

Create a hidden field to hold the primary key of the item you're selecting (so you don't have to depend on searching against a 'name' field or something else equally brittle):

```python
    title_pk = forms.IntegerField(widget=forms.HiddenInput())
```

Create a view to populate the autocomplete list:

```python
    def title_lookup(request):
        results = []
        if request.method == "GET":
            if request.GET.has_key(u'q'):
                value = request.GET[u'q']
                # Ignore queries shorter than length 3
                if len(value) > 2:
                    model_results = Title.objects.filter(name__icontains=value)
                    results = [ (x.__unicode__(), x.id) for x in model_results ]
        json = simplejson.dumps(results)
        return HttpResponse(json, mimetype='application/json')
```

This will, of course, need a URLconf:

```python
    url(r'^title_lookup/$', view=title_lookup, name='title_lookup'),
```

And to finish it off, a bit of JavaScript in your template to call the plugin:

```javascript
    <script>
        $(function() {
            $('#id_title').autocomplete('{% url title_lookup %}', {
                dataType: 'json',
                width: 500,
                parse: function(data) {
                    return $.map(data, function(row) {
                        return { data:row, value:row[1], result:row[0] };
                    });
                }
                }).result(
                    function(e, data, value) {
                        $("#id_title_pk").val(value);
                    }
                );
            }
        );
    </script>
```

### Sources

- [The Plugin][jqac]
- [Using JQuery with Django for Autocomplete][tut]
- [JTJ](http://postpostmodern.com)

[jqac]: http://bassistance.de/jquery-plugins/jquery-plugin-autocomplete/
[tut]: http://lethain.com/entry/2007/dec/01/using-jquery-django-autocomplete-fields/
