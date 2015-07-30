---
layout: default
title: Working with Images
modal-id: working-with-images
category: best-practices
---
Images must be the number one culprit in terms of slow downloads from the server. Any image that runs through our Liquid filters will get compressed. Here's some ways you can achieve this:

{% highlight html %}
{% raw %}
<img src="{{ portal.website_logo | url_for_portal_logo : "200x200" }}" />

<img src="{{ portal.website_logo | url_for_portal_logo : "_x_" }}" />

<img src="{{ portal.website_logo | url_for_portal_logo : "200x_" }}" />

<img src="{{ portal.website_logo | url_for_portal_logo : "_x200" }}" />
{% endraw %}
{% endhighlight %}

Basically any size dimensions or our nifty ``x`` function will see the image pass through the filters. Also don't forget to resize images. For example, it would be pointless dragging back a full size photo when all you need is a thumbnail for an article preview.