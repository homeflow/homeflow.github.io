---
layout: default
title: Content blocks
modal-id: content-blocks
category: application-and-homepage
---
Content blocks allow dynamic insersion of images, text or html into the site on a agency by agency basis.

Content blocks are called by name, and in their most basic from, rendered out like this

{% highlight liquid %}
{% raw %}
{% content_block 'a_nice_content_block' %}
 {% if content_block %}
  {{content_block}}
 {% endif %}
{% endcontent_block %}
{% endraw %}
{% endhighlight %}

Each time the content block tag is used it will yeild the following variabled

- `content_block` : prerendered content. If the content block includes an image that will be placed in an <img> tag.
- `content_block_found` :  A boolean usable for testing if the content block should be showed
- `content_block_url`
- `content_block_image`
- `content_block_title`

###Multiple content blocks

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

In this case, `content_block_found` will be true if more than 0 content blocks have been found. Additionally an array of
content block objects will be returned.

###Geo Content blocks

Geo content blocks are those containing a lat/lng pair. Any objects which respond to #lat or #lng can be used to query for
content blocks near that area. For instance, to get all 'ad_unit' content blocks near a set location on a page like `brighton-and-hove/brighton/sales`:

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
