---
layout: default
title: Custom branch pins
modal-id: custom-branch-pins
category: maps
---
Similar to the custom property pin function, using the branch object you can change the pin depending on branch attributes. You can set any available branch attribute in ``branches/_branch.ljson`` for single branch pages, or ``branches/_branches_list.ljson`` for the index of branches. As with the property pin, you'll need to declare the default settings.

If you only need one custom pin for all maps, please use the [custom map pins](/mapping/#custom-map-pins) code instead. 

{% highlight javascript %}
{% raw %}

Ctesius.addConfig('custom_branch_pin', function(branch){

 // set defaults if theme_preferences not set

 var markerIconImage = Ctesius.getConfig('root_url') + 'assets/leaflet/marker-icon.png';
 var markerIconSize = [25,41];
 var markerShadowUrl = Ctesius.getConfig('root_url') + 'assets/leaflet/marker-shadow.png';
 var markerShadowSize = [41,41];
 var channel;

 branch.get('sales_enabled') ? channel = branch.get('sales_enabled') : channel = '{{branch.sales_enabled}}';

 if ( channel == true ) {
  markerIconImage = '{{ 'sales_pin.png' | theme_image_url }}';
 } else {
  markerIconImage = '{{ 'lets_pin.png' | theme_image_url }}';
 }
 
 {% if theme_preferences.map_pin_marker_shadow %}
  markerShadowUrl = '{{ theme_preferences.map_pin_marker_shadow  | url_for_site_asset }}';
 {% endif %}

 {% if theme_preferences.map_pin_marker_shadow_size %}
  markerShadowSize = '{{ theme_preferences.map_pin_marker_shadow_size }}'.split(',');
 {% endif %}

 return new L.Icon.Default({
  iconUrl: markerIconImage,
  iconSize: markerIconSize,
  shadowUrl: markerShadowUrl,
  shadowSize: markerShadowSize
 })

});

{% endraw %}
{% endhighlight %}

Common fields to configure the pin on might include:

{% raw %}
- ``sales_enabled: {{branch.sales_enabled}}``
- ``lettings_enabled: {{branch.lettings_enabled}}``
- ``name: {{branch.name}}``
- ``branch_id : {{branch.branch_id}}``
{% endraw %}
