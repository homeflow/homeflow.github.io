---
layout: default
title: Vendor Assets
modal-id: assets
category: assets
---

You can configure the assets which are included in your theme in your ``config.yml`` with the ``asset_packs`` and ``vendor_assets`` configuration options.

**Asset packs**

These are the javascript and css files which you have included in the ``/assets`` directory in your theme.

Here is an example configuration:

{% highlight html %}

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

The ``vendor_assets`` configuration defines the assets which are bundled with your theme, you should include ``asset_pack`` in both the Javascript and css configurations to include your theme assets which you defined previously. You can choose which assets you would like to require from the Ctesius asset packs.

For a full reference of the Ctesius asset packs and the files they include [click here](/appendix/application-assets).

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
