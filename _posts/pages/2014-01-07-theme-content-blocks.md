---
layout: default
title: Theme content blocks
modal-id: theme-content-blocks
category: pages
---
When you want to define your own content blocks, this is where ``theme content chunks`` come in. Your first step here is to make the Homeflow backend aware that there is a chunk available. To do this we use the theme's YAML file:

{% highlight yaml %}
  site_content_chunks:
    - name: 'cms_sidebar_content'
      description: 'A custom sidebar content section for CMS pages.'
{% endhighlight %}

Once your theme gets publised, you can then navigate to your agency admin, visit ``/configure/website/content/site_content_chunks``, and add your content chunk for the agency with any associated HTML/content etc.

To marry any page to one or more of the blocks you have created and populated with content, we can loop over the content items of the CMS page:

{% highlight liquid %}
{% raw %}
{% for content_item in cms_page.content_items %}
    {% content_block content_item %}
        {{ content_block }}
    {% endcontent_block %}
{% endfor %}
{% endraw %}
{% endhighlight %}

You can associate a page with a chunk by navigating to the page on the CMS or direct using the following link: ``/configure/website/content/pages/9381/site_content_chunks`` (replace the ID with the page ID if known).