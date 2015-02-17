---
layout: default
title: The properties loop
modal-id: properties-loop
category: property-searching
---
Since Liquid for loops can include a partial for each property it makes sense to include a tried, tested and mananageble partial of code for each property. We refer to this partial as ``_property_small.liquid``.

Here's what our for loop looks like:

{% highlight html %}
{% raw %}
{% for property in properties %}
 {% include "properties/property_small" %}
{% endfor %}
{% endraw %}
{% endhighlight %}

As you can see we loop through the properties array and include the ``_property_small`` partial for each one. Let's now take a look at what a sample ``_property_small.liquid`` could look like:

{% highlight html %}
{% raw %}
<div id="property_{{property.property_id}}" class="property-small">
 {{ property | photo_overlay }}
 <a href="{{property | url_for_property}}">
  <img src="{{ property.photos.first | url_for_property_asset: "176x133" }}">
 </a>
 <a href="{{property | url_for_property}}">
  {{property.display_address | truncate : 60}}
 </a>
 <p>{{property.price}}</p>
 <p>{{property.short_description | truncate : 185}}</p>
 <p><a href="{{property | url_for_property}}">Full details</a></p>
</div>
{% endraw %}
{% endhighlight %}

- ``{% raw %}property_{{property.property_id}}{% endraw %}`` - outputs the unique ID of the property

- ``{% raw %}{{ property | photo_overlay }}{% endraw %}`` - outputs the property status in the form of an image banner. You can customise this in your agency or portal admin with the following link: ``/configure/website/appearance/custom_images``.

- ``{% raw %}{{ property.photos.first | url_for_property_asset: "176x133" }}{% endraw %}`` - gets the first photo from the property.photos array and resizes to the specified dimensions.

-  {% raw %}``{{property | url_for_property}}{% endraw %}`` - outputs the relative address to the property

- ``{% raw %}{{property.display_address | truncate : 60}}{% endraw %}`` - this tag outputs the display address of the property.

- ``truncate : 60`` - truncates the output to 60 characters. Another useful truncate function is ``truncatewords: 20``.