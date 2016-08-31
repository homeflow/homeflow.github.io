---
layout: default
title: Property Drop
modal-id: property-drop
category: drops
---
#### available_on
**Returns:** If supplied, the date the property is available.

#### bathrooms
**Returns:** An integer for number of bathrooms that sometimes comes in as zero or empty so needs to be checked.

#### bedrooms
**Returns:** An integer for bedroom count that sometimes comes in as zero or empty so needs to be checked.

#### brochures
**Returns:** This for loop would output all the brochures supplied.<br/>
**Example use:**
{% highlight html %}
{% raw %}
{% for brochure in property.brochures %}
 <li><a href="{{ brochure | url_for_property_asset }}">Download brochure</a></li>
{% endfor %}
{% endraw %}
{% endhighlight %}

#### description
**Returns:** The full Property description

#### epc_charts
**Returns:** This for loop would output all the EPC charts supplied.<br/>
**Example use:**
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

#### features
**Returns:** A list of property features that can be outputted to bullet points.

#### floorplans
**Returns:** The collection of floor plans. This loop could output the floor plans to a light box e.g Fancybox, Colorbox, etc.<br/>
**Example use:**
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

#### property_ref
**Returns:** The agent's supplied property reference.

#### reception_rooms
**Returns:** A numerical figure that sometimes comes in as zero or empty so needs to be checked.

#### road_name
**Returns:** The Property's road name

#### tags
**Returns:** An array of the tags set for the property

#### vox_number
**Returns:** Homeflow is able to generate recorded telephone numbers for properties. Doing a check on this drop can see whether one is available.
