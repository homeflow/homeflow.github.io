---
layout: default
title: Property results location pages
modal-id: location-pages
category: location-guides
---
In this example we can search the nodes for the location page and return all of the node items for that node. So this means for a location page we can return content such as local branch information, content_chunks, properties and more for the area guide. 

You need only assign the node once to URL if using multiple blocks on a page:

{% highlight html %}
{% raw %}
{% assign hf_node = 'slug-name' | location_node_by_slug %}
{% endraw %}
{% endhighlight %}

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


