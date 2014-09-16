---
layout: default
title: Recent sales and lettings
modal-id: recent-sales-and-lettings
categories: working-with-branches
---
Now we have our tabs, we can add the area that will be toggled on a click. Here's what a togglable sales tab and recent branch sales function looks like:

{% highlight html %}
{% raw %}
{% if branch.recent_sales_properties != empty %}
<script>
 {% assign properties = branch.recent_sales_properties %}
 sales_property_for_config = {% include_as_json properties/properties_list %}.properties
</script>
<div id="togglable_sales" class="togglable_area clearfix hidden">
<h2>Latest sale listings for {{branch.name}}</h2>
 {% for property in branch.recent_sales_properties limit: 20 %}
  {% include "properties/property_small" %}
 {% endfor %}
</div>
{% endif %}
{% endraw %}
{% endhighlight %}

Here we're making us of one of Ctesius's many built-in functions - this one gets recent properties that the branch has added or we have received via a feed. To get this up and running we literally call the function which returns the JSON we need. We then use the good ol' properties loop to output the results, whilst reusing our ``property_small``. Note that we've wrapped this whole block in an IF statement that checks if the function returns empty. It would be good practice to hide the link to the tab if the function has no results too.

To get this up and running for lettings, just substitute any reference to sales for lettings.