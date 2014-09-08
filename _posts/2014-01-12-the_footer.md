---
layout: default
title: The footer
modal-id: the-footer
---
Again, the footer is an area where you can hardcode in your design and content, or you can manage the content using the Agent/Portal admin and the ``content chunks`` we have made available. ``Content chunks`` are well-known content areas that get used on all sites - e.g. a header, footer, sidebar and so on. If we add some content to the footer chunk we can then render it out.

Agencies: ``Website/Content``<br>
Portals: ``Configure/Content/Pages``

Both content chunk sections are then on the left. Checkout the ``Site footer`` chunk, add some filler content for now then save it.

Now, where you want to render the chunk in your source (if it's the footer then most likely the ``application.liquid`` page), use the following code:

{% highlight html %}
{% raw %}
{% content_block 'site_footer' %}
 {% if content_block %}
  {{content_block}}
 {% endif %}
{% endcontent_block %}
{% endraw %}
{% endhighlight %}

This will render your chunk. Note that you can add HTML syntax into the chunk using the MCE editor.