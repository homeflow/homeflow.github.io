---
layout: default
title: Displaying search results
modal-id: displaying-search-results
categories: property-searching
---
After the form has been submitted, Ctesius and Hestia will go off an fetch the results - normally ten per page though this is configurable. A JSON response is returned and Liquid loops through and displays the results.

The first file we will want to get up and running is the ``properties/index.liquid`` file, which is located in the ``properties`` folder. The index displays every property belonging to an agency or portal. All searches are channel based so an index could show all sales or all lettings. On the whole the index will check whether the ``properties`` JSON is empty and if not, it will then include a ``_results.liquid`` partial, which is the main body of code that we'll be working with.

So the code could look something like this:

{% highlight html %}
{% raw %}
{% if properties == empty %}
  <h4>Sorry, we couldn't find any properties for this search.</h4>
 {% else %}
  {% include 'search/results' %}
{% endif %}
{% endraw %}
{% endhighlight %}

Note that in our example above we've put our ``results`` partial in a ``search`` sub-folder. You don't have to do this and your ``results`` partial could reside in the ``properties`` folder if you wish.

Our ``results`` partial will probably include top and bottom pagination, top and/or bottom search statistics, alternative view types (list, map, grid, etc) and of course the Liquid loop that displays the properties. Note that one, more or indeed all of the above can be partials so we can re-use them if necessary.