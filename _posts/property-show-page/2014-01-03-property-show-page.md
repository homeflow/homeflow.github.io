---
layout: default
title: Working with maps
modal-id: working-with-maps
category: property-show-page
---
Many developers employ the tabbing system for property maps so the user can cycle through the different types: road, streetview and satellite. The first requirement is some events:

{% highlight html %}
{% raw %}
<script>
 Ctesius.addConfig('small_map_element', 'contact_map')
 Ctesius.registerEvent('render_tab', function(tab_name){
  switch(tab_name){
   case 'streetview':
    {{ gmap_for property as streetview in streetview }}
    break;
   case 'satellite':
    {{ gmap_for property as satellite in satellite }}
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