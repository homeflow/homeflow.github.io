---
layout: default
title: Property results location blocks
modal-id: results-location-blocks
category: nodes
---
In this example we can search the nodes for the location page and return all of the node items for that node. So this means for a results location page, we can return content such as local branch information, content_chunks, properties and more for the area guide. The location must be assigned to the node in the backend before the location node can be queried.

Branch node:

{% highlight html %}
{% raw %}
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

Site content chunk node:

{% highlight html %}
{% raw %}
<div class="node">
 {% with_node hf_node, type: sitecontentchunk %}
  {% for node_item in node_items %}
   {{node_item.content}}
  {% endfor %}
 {% endwith_node %}
</div>
{% endraw %}
{% endhighlight %}

Property node:

{% highlight html %}
{% raw %}
<div class="node">
 {% with_node hf_node, type: property %}
  {% for node_item in node_items %}
   {{node_item.display_address}}
  {% endfor %}
 {% endwith_node %}
</div>
{% endraw %}
{% endhighlight %}

If you want to you want grab a specific node by slug, you can use the following assign statement, then use the blocks above:

You need only assign the node once to the slug if using multiple blocks on a page:

{% highlight html %}
{% raw %}
{% assign hf_node = 'slug-name' | location_node_by_slug %}
{% endraw %}
{% endhighlight %}

Don't forget that node items have access to the node type's drop methods. For example, the property drop methods can be found [here](/drops/#property-drop).
