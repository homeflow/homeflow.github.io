---
layout: default
title: Togglable areas
modal-id: togglable-areas
---
The core ``application javascript include`` comes with a JavaScript toggle system that can show and hide different ``tabs`` on a click. This is useful when working with different views and, as we will see later, it is also very useful on the ``property show`` page.

There are at least three well defined view types for the results page. They are ``list``, ``grid`` and ``map``. Here's what the code might look like:

{% highlight html %}
{% raw %}
<div id='togglable_list' class='togglable_area'>
 {% include 'properties/properties_list' %}
</div>
<div id="properties_grid_toggle_view" class="hidden togglable_area">
 {% include 'properties/properties_grid' %}
</div>
<div id='togglable_map' class='togglable_area hidden'>
 {% include 'properties/pagination_for_map' %}
 <div id='draggable_map_view'></div>
</div>
{% endraw %}
{% endhighlight %}

Then to link to the views, we simply use the hash reference in the anchor like so:

{% highlight html %}
<li><a href="#home" class="active">LIST</a></li>
<li><a href="#grid">GRID</a></li>
<li><a href="#map">MAP</a></li>
{% endhighlight %}

Note that ``#home`` correlates to the default list view.