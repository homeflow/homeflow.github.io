---
layout: default
title: Working with map views
modal-id: working-with-the-map-view
category: property-searching
---
Ctesius comes loaded with maps for property results, individual properties, branches and so on. A draggable map is at your disposal for property results. The draggable map view can be placed on the map tab outlined above and can also update the property results on the fly based on the user dragging or zooming. To get the map up and running, all you need to do is add the ``draggable_map_view`` div to your tab and supply it with a height and a width in your CSS:

``<div id='draggable_map_view'></div>``

Given that we're allowing the user to zoom and drag, it would be useful to have a dialogue of the current properties that are on display. It would also be useful to update this when the user interacts with the map. With Ctesius's built in event system, we can do just that.

Above the ``draggable_map_view`` div, you will see we have an include for map pagination. This is where we can add any map related dialogue we have. In our example below it's actually very little:

{% highlight html %}
{% raw %}
<span id='map_info'></span>
{% include 'properties/pagination_links' %}
{% endraw %}
{% endhighlight %}

Here we have an empty div ready to be populated with our dynamic map information and we have a partial to include the list, grid and map links that are common to all of the views. All we need to add to get the map information is two ``Ctesius events``:

{% highlight html %}
{% raw %}
<script>
 Ctesius.registerEvent('before_draggable_map_updated',function(){
  $('#map_info').html('Updating map...')
 });

 Ctesius.registerEvent('draggable_map_updated',function(res){
  $('#map_info').html('Showing ' + res.properties.length + ' of ' + res.pagination.total_count + ' properties. Zoom in or drag the map to see more.' )
 });
</script>
{% endraw %}
{% endhighlight %}

Ctesius ``kicks`` events throughout the execution of a theme that we can conveniently get a handle on and perform some kind of action. In our example above, we register a callback function to execute when our draggable map events are kicked. By doing this we can add some nice feedback to the user. You can add these functions anywhere you like though many developers add them to the ``js_event_registers`` partial, which resides in the ``layouts`` folder.