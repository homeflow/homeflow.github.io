---
layout: default
title: Content blocks
modal-id: content-blocks
category: cms-pages
---
Regularly used on content pages (but also elsewhere on a theme), content blocks allow dynamic insertion of content on an agency by agency basis. A number of stock content blocks exist (e.g the footer block), but you can also [create your own](/cms-pages#theme-content-blocks) and output where required. Log on to your agency admin and navigate to ``/configure/website/content/content/list`` to see the full list.

Content blocks are called by name and in their most basic form are rendered out to a page as follows:

{% highlight liquid %}
{% raw %}
{% content_block a_nice_content_block %}
 {% if content_block %}
  <div data-content-id="{{ content_block_id }}" data-content-type="site_content_chunks">
    {{content_block}}
  </div>
 {% endif %}
{% endcontent_block %}
{% endraw %}
{% endhighlight %}

Each time the content block tag is used it will yield the following variables:

{% raw %}
- ``{{content_block}}`` - a pre-rendered content. If the content block includes an image that will be placed in an ``img`` tag. If a URL is provided, the entire chunk will hyperlinked.

- ``{{content_block_found}}`` - a boolean used for testing if the content block is found

- ``{{ content_block_title }}``
      
- ``{{ content_block_text }}``
      
- ``{{ content_block_url }}``

- ``{{ content_block_id }}``
{% endraw %}

The content-id and content-type data attributes are used to link the content chunks to the relevant Logos page for editing.

And to retrieve the full image path:

{% highlight html %}<img src="{% raw %}{{ content_block_image | url_for_generic_image}}{% endraw %}" />{% endhighlight %}

Finally, one other useful function is to test for the chunk and output some kind of alternative:

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
