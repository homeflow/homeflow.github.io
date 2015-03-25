---
layout: default
title: Custom map pins
modal-id: custom-map-pins
category: mapping
---
The Ctesius app allows you to customise your theme's map pins and shadows using the settings that can be found in the agency's admin preferences section. To pull out the pin and shadow in code and apply to all Leaflet maps, here's what you'll need:

{% highlight liquid %}
{% raw %}

{% if theme_preferences.map_pin_marker_asset  %}
 Ctesius.addConfig('custom_map_icon', '{{ theme_preferences.map_pin_marker_asset | url_for_site_asset }}');
{% endif %}

{% if theme_preferences.map_pin_marker_size %}
 var dimensions = "{{ theme_preferences.map_pin_marker_size }}".split(',');
 Ctesius.addConfig('custom_map_icon_size', dimensions);
{% endif %}

{% if theme_preferences.map_pin_marker_shadow %}
 Ctesius.addConfig('custom_map_icon_shadow', '{{ theme_preferences.map_pin_marker_shadow | url_for_site_asset }}');
{% endif %}

{% if theme_preferences.map_pin_marker_shadow_size %}
 var shadow_dimensions = "{{theme_preferences.map_pin_marker_shadow_size}}".split(',');
 Ctesius.addConfig('custom_map_shadow_icon_size', shadow_dimensions);
{% endif %}

{% endraw %}
{% endhighlight %}

Note that if the theme preference has not been set, we will apply the default Leaflet pin a shadow configuration.
