---
layout: default
title: Other property drops
modal-id: other-property-drops
category: appendix
---
``{% raw %}{{property.available_on}}{% endraw %}``

If supplied, the date the property is available.

{% highlight html %}
{% raw %}
{% for feature in property.features %}
 {{ feature }}
{% endfor %}
{% endraw %}
{% endhighlight %}

A list of property features that can be outputted to bullet points.

``{% raw %}{{property.description}}{% endraw %}``

The full description.

``{% raw %}{{property.road_name}}{% endraw %}``

The property's road name.

``{% raw %}{{ property.vox_number }}{% endraw %}``

Homeflow is able to generate recorded telephone numbers for properties. Doing a check on this drop can see whether one is available.

``{% raw %}{{property.bedrooms}}{% endraw %}``

A numerical figure that sometimes comes in as zero or empty so needs to be checked.

``{% raw %}{{property.bathrooms}}{% endraw %}``

As above.

``{% raw %}{{property.reception_rooms}}{% endraw %}``

As per bedrooms.

``{% raw %}{{property.property_ref}}{% endraw %}``

The agent's supplied property reference.

{% highlight html %}
{% raw %}
{% for floorplan in property.floorplans %}
 {% if forloop.first %}
  <a href="http://mr0.homeflow.co.uk/{{ floorplan.image }}" title="Floor plan">
  {% if property.floorplans.size == 1 %}
    View floor plan
   {% else %}
    View floor plans
  {% endif %}
  </a>
  {% else %}
   <a href="http://mr0.homeflow.co.uk/{{ floorplan.image }}" style="display:none;" title="Floor plan"></a>
 {% endif %}
{% endfor %}
{% endraw %}
{% endhighlight %}

The collection of floor plans. This loop could output the floor plans to a light box e.g Fancybox, Colorbox, etc.

{% highlight html %}
{% raw %}
{% for brochure in property.brochures %}
 <li><a href="{{ brochure | url_for_property_asset }}">Download brochure</a></li>
{% endfor %}
{% endraw %}
{% endhighlight %}

This for loop would output all the brochures supplied.

{% highlight html %}
{% raw %}
{% for epc_chart in property.epc_charts %}
 {% if forloop.first %}
  <a href="{{ epc_chart | url_for_property_asset }}">
  {% if property.epc_charts.size == 1 %}
   View EPC chart
  {% else %}
   View EPC charts
  {% endif %}
  </a>
 {% else %}
  <a href="{{ epc_chart | url_for_property_asset }}" style="display:none"></a>
 {% endif %}
{% endfor %}
{% endraw %}
{% endhighlight %}

As per above and floor plans.