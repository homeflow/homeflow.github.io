---
layout: default
title: Property pages
modal-id: property-pages
category: location-guides
---
Another powerful feature of the nodes architecture for Location Guides is you can link back through to any node that has a property as a node item. This means that property detail pages can find attached Location Guides and pull out any other node item associated with that Location Guide, such as a SiteContentChunk, a Branch and more. 

Just use the property_node_by_slug assignment method before the with_node block like so:

{% highlight html %}
{% raw %}
{% assign hf_node = ‘slug-name’ | property_node_by_slug %}
<h2>Found node from location then link to branch</h2>
<div class="node">
 {% with_node hf_node,  type: branch  %}
  {% for node_item in node_items %}
   Branch name is: {{node_item.name}}</br>
  {% endfor %}
 {% endwith_node %}
</div>
{% endraw %}
{% endhighlight %}