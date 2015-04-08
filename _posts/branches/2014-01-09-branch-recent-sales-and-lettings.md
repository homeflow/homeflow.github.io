---
layout: default
title: Branch recent sales and lettings
modal-id: branch-recent-sales-and-lettings
category: branches
---
Here's what a togglable sales tab and recent branch sales function looks like:

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

To get this up and running for lettings, just substitute any reference to sales for lettings.