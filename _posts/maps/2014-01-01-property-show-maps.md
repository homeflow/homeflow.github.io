---
layout: default
title: Property show maps
modal-id: property-show-maps
category: maps
---
Many developers employ the tabbing system for property maps so the user can cycle through the different types: road, streetview and satellite. The first requirement are some events:

{% highlight javascript %}
{% raw %}
<script>
 Ctesius.addConfig('small_map_element', 'contact_map')

 Ctesius.registerEvent('render_tab', function(tab_name){
  switch(tab_name){
   case 'streetview':
    {% gmap_for property as streetview in streetview %}
    break;
   case 'satellite':
    {% gmap_for property as satellite in satellite %}
    break;
   }
 });
</script>
{% endraw %}
{% endhighlight %}

The first line here adds our map to the ``contact_map`` ID or class (seen below). The ``render_tab`` event registers a callback function that renders the appropriate Google map depending on the tab clicked. We then have our anchors and togglable areas:

{% highlight html %}
<a class="selected" id="tab_map" href="#tabs/map">MAP</a>
<a id="tab_streetview" href="#tabs/streetview">STREETVIEW</a>
<a id="tab_satellite" href="#tabs/satellite">SATELLITE</a>
{% endhighlight %}

{% highlight html %}
<div id="togglable_map" class="togglable_area">
 <div id="contact_map"></div>
</div>
<div id="togglable_streetview" class="togglable_area hidden">
 <div id='streetview' class="google_map_container"></div>
</div>
<div id="togglable_satellite" class="togglable_area hidden">
 <div id='satellite' class="google_map_container"></div>
</div>
{% endhighlight %}

The render tab function renders gets the element's bounds on a click and loads the map. This allows the map to be renderered fully without any missing or skewed tiles. If you find that your map is not working and you're not using our tabbing system, you'll need to employ your own click function:

{% highlight javascript %}
{% raw %}
<script type="text/javascript">
 $('#property-detail-tabs a').on('click', function () {
  if($(this).attr('href') == '#togglable_streetview'){
   {% gmap_for property as streetview in streetview %}
  }
 });
</script>
{% endraw %}
{% endhighlight %}