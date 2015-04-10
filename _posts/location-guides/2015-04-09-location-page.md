---
layout: default
title: Property results location pages
modal-id: location-pages
category: location-guides
---
In this example we can search the nodes for the location page and return all of the node items for that node. So this means for a location page we can return content such as local branch information, content_chunks and more for the area guide. 

{% highlight html %}
{% raw %}
{% assign hf_node = 'slug-name' | location_node_by_slug %}
<h2>Found node from location then link to branch</h2>
<div class="node">
 {% with_node hf_node, type: branch %}
  {% for node_item in node_items %}
   Branch name is: {{node_item.name}}</br>
   ...
  {% endfor %}
 {% endwith_node %}
</div>
{% endraw %}
{% endhighlight %}