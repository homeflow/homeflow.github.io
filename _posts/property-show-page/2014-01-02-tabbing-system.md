---
layout: default
title: The tabbing system
modal-id: property-show-page
category: property-show-page
---
Many developers employ the tabbing system so the user can toggle through the different tabs that contain a full description, floor plans, EPC graphs and so on. Active and hidden classes are applied via the core app.

{% highlight html %}
<li><a href="#tabs/home" id="tab_home" class="selected">Photos</a></li>
<li><a href="#tabs/details" id="tab_details">Full details</a></li>
<li><a href="#tabs/map" id="tab_map">Map</a></li>
<li><a href="#tabs/satellite" id="tab_satellite">Satellite</a></li>
{% endhighlight %}

{% highlight html %}
<div id="togglable_home" class="togglable_area">
</div>

<div id="togglable_details" class="togglable_area hidden">
</div>

<div id="togglable_map" class="togglable_area hidden">
 <div id='single_map'></div>
</div>
  
<div id="togglable_satellite" class="togglable_area hidden">
 <div id='satellite' class="google_map_container"></div>
</div>
{% endhighlight %}