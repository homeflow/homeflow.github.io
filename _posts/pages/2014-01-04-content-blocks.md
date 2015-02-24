---
layout: default
title: Content blocks
modal-id: content-blocks
category: pages
---
Regularly used on content pages (but also elsewhere on a theme), content blocks allow dynamic insertion of content on an agency by agency basis. A number of stock content blocks exist (e.g the footer block), but you can also [create your own](/pages#theme-content-blocks) and output where required.

Content blocks are called by name and in their most basic form are rendered out to a page as follows:

{% highlight liquid %}
{% raw %}
{% content_block 'a_nice_content_block' %}
 {% if content_block %}
  {{content_block}}
 {% endif %}
{% endcontent_block %}
{% endraw %}
{% endhighlight %}

Each time the content block tag is used it will yield the following variables:

- `content_block` - a prerendered content. If the content block includes an image that will be placed in an <img> tag.
- `content_block_found` - a boolean usable for testing if the content block should be showed
- `content_block_url`
- `content_block_image`
- `content_block_title`

. Log on to your agency admin and navigate to ``/configure/website/content/content/list`` to see the full list.

Another useful function is to test for the chunk and output some kind of alternative:

{% highlight yaml %}
{% raw %}
{% content_block cms_sidebar %}
 {% if content_block %}
  {{ content_block }}
 {% else %}
  alternative output
 {% endif %}
{% endcontent_block %}
{% endraw %}
{% endhighlight %}
