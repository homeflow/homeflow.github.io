---
layout: default
title: Vendor Assets
modal-id: application-assets
category: assets
---

You can configure the assets which are included in your theme in you {% highlight html %} config.yml {% endhighlight %} with the {% highlight html %} asset_packs {% endhighlight %} and {% highlight html %} vendor_assets {% endhighlight %} configuration options.

**Asset packs**

These are the javascript and css files which you have included in the {% highlight html %} /assets {% endhighlight %} directory in your theme.

Here is an example configuration:

{% hightlight html %}

asset_packs:
 javascript:
  - jquery.fancybox.js
  - main.js
 stylesheet:
  - photoswipe.lcss
  - style.lcss
  - custom.lcss

{% endhighlight %}

**Vendor Assets**

The {% highlight html %} vendor_assets {% endhighlight %} configuration defines the asset packs which are bundled with your theme, you should include {% asset_pack %} in both the Javascript and css configurations to include your theme assets which you defined previously. You can choose which assets you would like to require from the Ctesius asset packs.

You can see a full reference of the assets which are bundled with Ctesius [here](/appendix#application-assets).

Here is an example configuration:

{% highlight html %}

vendor_assets:
 javascripts:
  - ctesius
  - classic_extra
  - asset_pack
 stylesheets:
  - ctesius
  - asset_pack

{% endhighlight %}
