---
layout: default
title: Working with video
modal-id: working-with-video
category: property-show-page
---
Homeflow supports video across all themes and we provide handy helpers to extract and embed property videos into your show page without too much fuss. Note that the video URL needs to be in an incoming property feed for this to operate.

If you just want the video URL that's supplied in the feed, you can simply use:

{% highlight liquid %}
{% raw %}
{{ property.video_url }}
{% endraw %}
{% endhighlight %}

As it stands this will fish out a YouTube or Vimeo like URL for you. This output can be wrapped in an if statement should you want to check it's there before outputting.

Going a step further, if you would like to embed the video into the page, you can make use of one of our helper methods. These methods have an added benefit in that they can take non typical embed URLs like a YouTube 'watch' link or similar Vimeo link and turn it to an embed type link. The method below will create the iframe code for you and insert the video embed link:

{% highlight liquid %}
{% raw %}
{{ property.video_url | video_embed : 640, 390, 'iframe' }}
{% endraw %}
{% endhighlight %}

If you would rather just the link, but you'd like it to be the embed style for a lightbox, use this:

{% highlight liquid %}
{% raw %}
{{ property.video_url | video_embed : 640, 390, 'lightbox' }}
{% endraw %}
{% endhighlight %}

The method always expects some dimensions, even though they're not actually used for the lightbox style URL output - just add some arbitrary dimensions.