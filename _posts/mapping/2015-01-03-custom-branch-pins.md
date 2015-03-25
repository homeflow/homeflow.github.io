---
layout: default
title: Custom branch pins
modal-id: custom-branch-pins
category: mapping
---
Similar to the custom property pin function, using the branch object you can change the pin depending on branch attributes. You can set any available branch attribute in ``branches/_branch.ljson`` for single branch pages, or ``branches/_branches_list.ljson`` for the index of branches. As with the property pin, you'll need to declare the default settings.

If you only need one custom pin for all maps, please use the [custom map pins](/mapping/#custom-map-pins) code instead. 

{% highlight javascript %}
{% raw %}

Ctesius.addConfig('custom_branch_pin', function(branch){

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
  markerShadowUrl = Ctesius.addConfig('custom_map_icon_shadow', '{{ theme_preferences.map_pin_marker_shadow  | url_for_site_asset }}');
 {% endif %}

 {% if theme_preferences.map_pin_marker_shadow_size %}
  markerShadowSize = Ctesius.addConfig('custom_map_shadow_icon_size', '{{ theme_preferences.map_pin_marker_shadow_size }}');
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

Common fields to configure the pin on would be the branch channel settings:

{% raw %}
- ``sales_enabled: {{branch.sales_enabled}}``
- ``lettings_enabled: {{branch.lettings_enabled}}``
- ``name: {{branch.name}}``
- ``branch_id : {{branch.branch_id}}``
{% endraw %}
