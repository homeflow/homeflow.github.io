---
layout: default
title: Displaying search results
modal-id: displaying-search-results
category: property-searching
---
After the form has been submitted, Ctesius and Hestia will go off an fetch the results - normally ten per page though this is configurable. A JSON response is returned and Liquid loops through and displays the results.

The first file we will want to get up and running is the ``properties/index.liquid`` file, which is located in the ``properties`` folder. The index displays every property belonging to an agency or portal. All searches are channel based so an index could show all sales or all lettings.

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

Next we need to add the properties loop to search/results.