---
layout: default
title: Agency recent sales and lettings
modal-id: agency-recent-sales-lettings
category: agencies
---
There are three recent property related functions to be aware of:

- Recent properties
- Recent sales properties
- Recent lettings properties

Whereas recent properties gets both sales and lettings, recent sales or recent lettings gets five properties belonging to the respective channel. They are all called in much the same way and make use of the same fields. Here's how to call the recent sales function:

{% highlight html %}
{% raw %}
{% for property in agency.recent_sales_properties %}
 <a href="{{property | url_for_property}}">
  <h3>New Listings</h3>
  <h4>{{property.primary_address_display}}</h4>
  <img src="{{property.photos.first | url_for_property_asset }}" />
 </a>
{% endfor %}
{% endraw %}
{% endhighlight %}

