---
layout: default
title: Geo Content blocks
modal-id: geo-content-blocks
category: pages
---
Geo content blocks are those containing a lat/lng pair. Any objects which respond to #lat or #lng can be used to query for content blocks near that area. For instance, to get all 'ad_unit' content blocks near a set location on a page like `brighton-and-hove/brighton/sales`:

{% highlight liquid %}
{% raw %}
{% content_block 'ad_unit' multiple:true location:location %}
 {% for block in content_blocks limit: 3 %}
  <h3>{{block.content_block_title}}</h3>
  <img src="{{block.content_block_title}}"/>
 {% endfor %}
{% endcontent_block %}
{% endraw %}
{% endhighlight %}