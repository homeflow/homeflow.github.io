---
layout: default
title: CSS Pre-processors
modal-id: css-preprocessors
category: application-and-homepage
---
At the time of writing, the Ctesius app supports the [LESS CSS pre-processor](http://lesscss.org/). We will extend the app further in the future to support SASS. For now, to get up and running with LESS, simply add your CSS file with the ``lless`` extension to your theme's CSS folder. You can then bring it into the theme and have it processed using the following line:

{% highlight liquid %}
{% raw %}
{{ "stylesheet_name" | theme_less_stylesheet_link_tag }}
{% endraw %}
{% endhighlight %}