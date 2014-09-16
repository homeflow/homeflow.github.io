---
layout: default
title: The properties loop
modal-id: properties-loop
categories: property-searching
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

Let's step through this. As you can see, we need to wrap each set of results in an ID or class container and we'll need to style up the elements so it renders nicely on a row. We'll assume you are okay with that and explain the Liquid.

Firstly, the ID of the div is ``{% raw %}property_{{property.property_id}}{% endraw %}``. As you can imagine, every property in our system gets assigned a numerical ID, and it's this ID that's used in URL and for other functions on the theme and in the backend. For now, we've outputted the ID so we can use our ``Save to shortlist`` function - more on that later.

The next tag ``{% raw %}{{ property | photo_overlay }}{% endraw %}`` outputs the property status in the form of a sash image banner, or a custom banner of your choice. You can get to this custom images section via your agency or portal admin with the following link: ``/configure/website/appearance/custom_images``.

The next piece of Liquid is: ``{% raw %}{{ property.photos.first | url_for_property_asset: "176x133" }}{% endraw %}``. As you might imagine, this looks at the photos array and gets the link of the first one for use in the image source. We then use the ``url_for_property_asset`` key and we pass in a size in pixels. As mentioned before, Liquid will resize the image on the server and send it to the browser.

A tag that's used numerous times in this code, as well as on many of the property related pages; ``{% raw %}{{property | url_for_property}}{% endraw %}`` outputs the relative address to the property in question.

The next tag is ``{% raw %}{{property.display_address | truncate : 60}}{% endraw %}``. This tag outputs the display address of the property, which is the address as it comes in from the agency or portal feeds. A new arguement seen here is ``truncate``. This is a very useful Liquid function, which is particularly useful when curtailing long addresses, descriptions and so on - just pass in the number of characters you want to keep. Another useful truncate function is ``truncatewords: 20``. This does what it says on the tin.