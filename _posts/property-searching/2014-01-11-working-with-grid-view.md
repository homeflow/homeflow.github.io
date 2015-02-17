---
layout: default
title: Working with grid views
modal-id: working-with-grid-views
category: property-searching
---
The easiest way to get up and running with a grid view is to have a ``properties_grid`` partial that sits in the togglable grid container. Within this partial there is a second properties loop:

{% highlight html %}
{% raw %}
 <div id="properties_grid_toggle_view" class="hidden togglable_area">
  {% for property in properties %}
   {% include 'properties/properties_grid' %}
  {% endfor %}
 </div>
{% endraw %}
{% endhighlight %}

Another alternative is to use JavaScript to show/hide/tweak the list and grid layouts on the click of a link.