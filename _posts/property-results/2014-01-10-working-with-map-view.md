---
layout: default
title: Working with map views
modal-id: working-with-the-map-view
category: property-results
---
To get the map up and running, all you need to do is add the ``draggable_map_view`` div to your tab and supply it with a height and a width in your CSS:

``<div id='draggable_map_view'></div>``

Note that if the draggable map doesn't sit in the map container, be sure to call ``#map`` is the URL for it to display.

Given that we're allowing the user to zoom and drag, it would be useful to have a dialogue of the current properties that are on display:

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

For more on events, visit the [events section](/events).