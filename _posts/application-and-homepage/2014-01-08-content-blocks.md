---
layout: default
title: Content blocks
modal-id: content-blocks
category: application-and-homepage
---
Content blocks allow dynamic insertion of images, text or html into the site on an agency by agency basis.

Content blocks are called by name and in their most basic form are rendered out like this:

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

A number of stock content blocks exist within the Homeflow system that you can output in various places. Log on to your agency admin and navigate to ``/configure/website/content/content/list`` to see the full list.

###Theme content chunks

When you want to define your own content blocks, this is where ``theme content chunks`` come in. Consider a scenario where an agency asks for a content area that they can be edited from time to time. Let's imagine that your site is also a theme for multiple agencies and that not all agencies will want or need to update the block, or even have the block outputted at all. This is where theme content chunks come into their own.

Your first step here is to make the Homeflow backend aware that there is a chunk available. To do this we use our trusty YAML file. In here, you might have something like:

{% highlight yaml %}
  site_content_chunks:
    - name: 'location_pod'
      description: 'A custom sidebar content section for CMS pages.'
{% endhighlight %}

Once your theme gets published, you can then navigate to your agency admin, visit ``/configure/website/content/site_content_chunks`` and add your content chunk for the agency with any associated HTML/content etc.

If your chunk was called ``cms_sidebar`` we would render it out in the theme thusly:

{% highlight yaml %}
{% raw %}
{% content_block home_intro %}
 {{ content_block }}
{% endcontent_block %}
{% endraw %}
{% endhighlight %}

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

In this case, `content_block_found` will be true if more than zero content blocks have been found. Additionally an array of content block objects will be returned.

###Geo Content blocks

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
