---
layout: default
title: CSS pre-processors
modal-id: css-preprocessors
category: application-and-homepage
---
At the time of writing, the Ctesius app supports the [LESS CSS pre-processor](http://lesscss.org/). We will extend the app further in the future to support SASS. For now, to get up and running with LESS, simply add your CSS file with the ``lless`` extension to your theme's CSS folder. You can then bring it into the theme and have it processed using the following line:

{% highlight liquid %}
{% raw %}
{{ "stylesheet_name" | theme_less_stylesheet_link_tag }}
{% endraw %}
{% endhighlight %}

If you would like to use SASS or another compiler, there is nothing to stop you running your compiler of choice locally, whilst configuring it to generate an LCSS file which is then pushed to the repo and referenced in your theme.