---
layout: default
title: Location guide show
modal-id: location-guide-show
category: location-guides
---
On the location guide show page you can access all the node items for that node (which remember is what a location guide is).

You can call a node with either {{node}} or {{hf_node}} as they are one in the same thing, however note that the with_node block (mentioned below) expects hf_node to be passed into it - this is due to liquid markup also using the variable 'node' so things get confused and sad in our rendering engine.

You can access the node items of a specific type by using the with_node block helper like so:

{% highlight html %}
{% raw %}
{% with_node hf_node, type: sitecontentchunk, name: hero_intro  %}
  {% for node_item in node_items %}
   <p>{{node_item.content}}</p>
  {% endfor %}
{% endwith_node %}
{%endraw%}
{% endhighlight %}

For more information on nodes click [here](/nodes).
