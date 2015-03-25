---
layout: default
title: Custom property pins
modal-id: custom-property-pins
category: mapping
---
If you would like complete control over the property pin, and to be able to create and return the Leaflet pin object yourself, you can use an ``addConfig`` with a callback function. Because this function takes the property object as an arguement, and because each property will run through this function, you can customise the pin based on things like whether the property is sales, lettings, for sale, to let, sold and so on.

{% highlight javascript %}
{% raw %}

Ctesius.addConfig('custom_property_pin', function(property) {
 var status;
 property.get('status') ? status = property.get('status') : status = '{{property.status}}';

 if (status == 'For sale' || status == "To let") {
  var markerIcon = "{{ theme_preferences.map_pin_marker_asset | url_for_site_asset }}";
 } else {
  var markerIcon = "{{ "sold_pin.png" | theme_image_url }}"
 }
       
 {% if theme_preferences.map_pin_marker_size %}
  var markerIconSize = "{{ theme_preferences.map_pin_marker_size }}".split(',');
 {% endif %}

 {% if theme_preferences.map_pin_marker_shadow %}
  var markerShadowUrl = "{{ theme_preferences.map_pin_marker_shadow | url_for_site_asset }}";
 {% endif %}

 {% if theme_preferences.map_pin_marker_shadow_size %}
  var markerShadowSize = "{{theme_preferences.map_pin_marker_shadow_size}}".split(',');
 {% endif %}

 return new L.Icon.Default({
  iconUrl: markerIcon,
  iconSize: markerIconSize,
  shadowUrl: markerShadowUrl,
  shadowSize: markerShadowSize
 })
});

{% endraw %}
{% endhighlight %}

Important point: if you choose this custom function and you are building a multi agency theme, you will need to code in a backup in case the theme preferences are not set. You may elect to assign the default values then override them if theme preferences are set:

{% highlight javascript %}
{% raw %}

var markerIcon = Ctesius.getConfig('root_url') + 'assets/leaflet/marker-icon.png';
var markerIconSize = [25,41];
var markerShadowUrl = Ctesius.getConfig('root_url') + 'assets/leaflet/marker-shadow.png';
var markerShadowSize = [41,41];

{% endraw %}
{% endhighlight %}

Any and all fields are populated from the ``properties/_properties_list.ljson`` file in the core app, unless you have your own custom version in theme. Some attributes you might like to configure the pin on include:

{% raw %}

- property_channel: {{property.primary_channel}} - 'sales' or 'lettings'
- status: {{ property.status}} - examples include - 'For sale', 'To let', 'Sold', 'SSTC', 'Let', Let agreed'
- property_type: {{property.property_type}}
- branch_name: '{{property.agency.branch.branch_name}}'

{% endraw %}

