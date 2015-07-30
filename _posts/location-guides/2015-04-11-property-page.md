---
layout: default
title: Property pages
modal-id: property-pages
category: location-guides
---
Any properties that are associated with nodes can be extracted; either directly by using the slug of the node, or by looping through all the nodes that have the property attached. This means that property detail pages can find attached Location Guides and pull out any other node item associated with that Location Guide, such as a SiteContentChunk, a Branch and more. 

To directly grab a node by slug name, you would do the following:

{% highlight html %}
{% raw %}
{% assign hf_node = 'slug-name' | property_node_by_slug %}
<h2>Found node from location then link to branch</h2>
<div class="node">
 {% with_node hf_node, type: branch %}
  {% for node_item in node_items %}
   Branch name is: {{node_item.name}}</br>
  {% endfor %}
 {% endwith_node %}
</div>
{% endraw %}
{% endhighlight %}

Or to loop through all nodes that are attached to a property:

{% highlight html %}
{% raw %}
{% for hf_node in location.nodes %}
  <div class="node">
   {% with_node hf_node, type: branch %}
    {% for node_item in node_items %}
     Branch name is: {{node_item.name}}</br>
    {% endfor %}
   {% endwith_node %}
  </div>
{% endfor %}
{% endraw %}
{% endhighlight %}

