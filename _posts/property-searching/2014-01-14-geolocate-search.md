---
layout: default
title: Geolocate Search
modal-id: geolocate-search
category: property-searching
---

To search for properties in the users current location, you can use the Geolocate search. Ctesius will use the Wifi connection, or GPS (if available) to find the current location and search for properties nearby.

To use this, simply add a button to your search form (below) which calls the `` geoLocate() `` function in its onClick event, this will search for your current location and populate the appropriate fields in the search form,

{% highlight html %}

  <a id="geolocate" onClick="Ctesius.Actions.geoLocate()"></a>

{% endhighlight %}
