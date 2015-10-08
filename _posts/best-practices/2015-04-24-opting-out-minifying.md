---
layout: default
title: Opting out and Minifying
modal-id: opting-out-minifying
category: best-practices
---
The Ctesius app is bundled with a bunch of JS and CSS, such as Bootstrap and Nivo Slider that many of our 'classic' themes still use (you can see a complete list [here](/appendix/application-js)). Many newer themes will call for updated versions of certain plugins that we might include, or they might not need them at all. Here's how to minify and filter out what you don't need.

In your theme's ``config.yml`` file, you will need a construct such as this:

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
vendor_assets:
 javascripts:
  - ctesius
  - asset_pack
 stylesheets:
  - asset_pack
{% endhighlight %}

Asset packs are your included stylesheets and JavaScripts. Vendor assets are includes for both core files and the asset packs you declared prior. The Ctesius vendor asset includes the bare minimum you need to build a theme on Homeflow, with no excess.

To output your minified JS and CSS in your theme, add the following two lines:

{% highlight html %}
{% raw %}
<head>
 <link href="/vendor_assets/blob.css" rel="stylesheet" type="text/css" />
</head>
{% endraw %}
{% endhighlight %}

{% highlight javascript %}
{% raw %}
    <script src='/vendor_assets/blob.js' type='text/javascript'></script>
 </body>
</html>
{% endraw %}
{% endhighlight %}