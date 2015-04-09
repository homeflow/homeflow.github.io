---
layout: default
title: Property pages
modal-id: location-pages
category: location-guides
---

Another powerful feature of the nodes architecture for LocationGuides is that you can link back through to any node that has a property as a node item. This means that on a property details page you can find attached LocationGuides and pull out any other node item associated with that LocationGuide such as a SiteContentChunk or a Branch and more. 

Just use the property_node_by_slug assignment method before the with_node block like so:

{% highlight html %}
{% raw %}
	{% assign hf_node = ‘slug-name’ | property_node_by_slug %}
	<h2>Found node from location then link to branch</h2>
	<div class="node">
	{% with_node hf_node,  type: branch  %}
	  {% for node_item in node_items %}
	    Branch name is: {{node_item.name}}</br>
		...
{% endraw %}
{% endhighlight %}