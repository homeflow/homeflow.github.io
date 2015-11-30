---
layout: default
title: Package and Minify
modal-id: package-and-minify
category: assets
---
The Ctesius app comes bundled with certain JS and CSS plugins, you can configure which are included or include your own in the ``config.yml`` file in your theme. These will then be bundled into the ``blob.js`` and ``blob.css`` files and included in the site. (you can see a list of available assets [here](/appendix/application-assets)).

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

Asset packs are the stylesheets and JavaScript files which you wish to include in your theme. The Vendor assets are the core asset packs you wish to include, ``asset_pack`` should be included here as these are the assets defined prior. The ``Ctesius`` vendor asset pack includes the bare minimum you need to build a theme on Homeflow, with no excess.

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
