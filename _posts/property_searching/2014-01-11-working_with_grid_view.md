---
layout: default
title: Working with grid views
modal-id: working-with-grid-views
categories: property_searching
---
At the time of writing many agencies are integrating grid views into their property results. Grid views can sometimes produce a better visual offering than traditional list views plus they offer the user a degree of presentation flexibility. The easiest way to get up and running with a grid view is to have a ``properties_grid`` partial. Within this partial there is a second properties loop:

{% highlight html %}
{% raw %}
{% for property in properties %}
 {% include 'properties/property_grid' %}
{% endfor %}
{% endraw %}
{% endhighlight %}

The partial ``property_grid`` then contains your individual grid view syntax. Since we're running another properties loop you might be forgiven to thinking we're fetching the properties again. Actually what we're doing is processing the same JSON that was returned from list view, so there is little or no overhead.