---
layout: default
title: Custom CSS
modal-id: custom-css
category: best-practices
---
It is best to use CSS that can be easily adapted for multiple site configurations using a range of different theme preference colours. The colour preferences page contains colours such as: ``primary_colour``, ``secondary_colour``, ``accent_colour`` etc and can be found in the backend at: ``../configure/website/appearance/colours``

These can be used in the css files in your theme as shown here:

{% highlight html %}
{% raw %}
header {
  background-color: {{ theme_preferences.header_background_colour }};
}
{% endraw %}
{% endhighlight %}

You can see a full list of the available colour options [here](/appendix/theme-colours).
