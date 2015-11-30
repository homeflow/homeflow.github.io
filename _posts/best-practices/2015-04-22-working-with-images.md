---
layout: default
title: Working with Images
modal-id: working-with-images
category: best-practices
---

**Image Formats**

It may seem obvious but choosing the right images are important for the efficiency of the theme and can affect the overall speed of the site.

It is advisable to pick the right type of image for the job.

**BMP** files shoud never be used. Ever.

**PNG** The Portable Network Graphics format was designed to be a lossless format for use on the WEB (among other things). It does reduce the size of your files. However since it preserves all the detail and all the colors the size reduction is not as much as GIF or JPG. This format is recommended for icons and small images and not large background images.

**JPG**. JPG stands for Joint Photographic Group, which is the name of the organization which created this format. JPG was designed for the storage of photographs and is in fact used in most digital cameras. It is lossy, so you do lose detail, but you can choose how much detail you lose.

**Flexable Image Size**

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

**Re-Themeable Images**

It is preferred that images are used that would not be incongruent if the theme colours were completely different. Try avoid using strong colours - perhaps using transparent icons with configurable background colours and/or white/grey shades would a good place to start.
