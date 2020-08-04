---
layout: default
title: Branch maps
modal-id: branch-maps
category: maps
---
Homeflow supports a variety of map types which you can extend with custom pins, overlays and so on. The first and easiest map to set-up is the Leafleft.js map type. To get this up and running on the branches index page, start by adding:

{% highlight html %}
{% raw %}
<script>
  Ctesius.addConfig('branch_map_element', 'branch_map');
  Ctesius.addConfig('branches', {% include_as_json branches/branches_list %});
</script>
{% endraw %}
{% endhighlight %}

Next we need to declare our ``div`` to apply the map to:

``<div id="branch_map"></div>``

Don't forget to give your map ID or class and height and/or width to get it to show up. This should be enough to get your Leaflet branch map showing with a pin for each branch. The map bubbles have a fairly basic presentation that's fine for most, but if you would like to customise your pin, you can override ``_branch_map_pin.liquid`` in your ``js_templates`` folder and customise the layout and styles as necessary.

### Google maps

If you would prefer a Google style map you still need the ``addConfig branches`` code seen before, but this time, instead of your ``addConfig branch_map``, we need:

``{% raw %}{% gmap_for agency.branches as roadmap in branch_map %}{% endraw %}``

This should then populate your ``branch_map`` div with a Google style map. Note that we're using the ``agency.branches`` ``drop`` to access the branches belonging to an agency. Please note that Google maps do not have pin popups and the customisation capabilites of Leaflet maps.

You can also use a Google tile layer over a leaflet map by adding the following config (ideally with your other config settings):

{% highlight html %}
{% raw %}
<script>
  Ctesius.addConfig('leaflet_layer', new L.Google('ROADMAP'));
</script>
{% endraw %}
{% endhighlight %}
