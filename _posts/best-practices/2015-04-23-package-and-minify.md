---
layout: default
title: Package and Minify
modal-id: package-and-minifying
category: best-practices
---
By minifying and packaging all JS and CSS into one file, we can call the file once and condense many resource calls into just one. The likes of Google PageSpeed will thank us for doing this.

In your theme's ``config.yml`` file, you will need a construct such as this with your files referenced:

{% highlight yaml %}
asset_packs:
 javascript:
  - vendor/bootstrap/transition.js
  - vendor/bootstrap/collapse.js
  - vendor/bootstrap/tab.js
  - main.js
 stylesheet:
  - styles.lcss
  - profile.lcss
  - photoswipe.lcss
  - custom.lcss
{% endhighlight %}

To output your minified JS and CSS in your theme, add the following two lines:

{% highlight html %}
{% raw %}
<script src="/liquid_assets/javascript_pack.js"></script>

<link href="/liquid_assets/stylesheet_pack.css" rel="stylesheet" type="text/css" />
{% endraw %}
{% endhighlight %}