---
layout: default
title: Multiple content blocks
modal-id: multiple-content-blocks
category: cms-pages
---
In some cases it's useful to be able to define a content block multiple times:

{% highlight liquid %}
{% raw %}
{% content_block 'ad_unit' multiple:true %}
 {% for block in content_blocks limit: 3 %}
  <h3>{{block.content_block_title}}</h3>
  <img src="{{block.content_block_title}}"/>
 {% endfor %}
{% endcontent_block %}
{% endraw %}
{% endhighlight %}

In this case, `content_block_found` will be true if more than zero content blocks have been found. Additionally an array of content block objects will be returned.
