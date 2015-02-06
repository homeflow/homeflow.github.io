---
layout: default
title: Properties from tag
modal-id: properties-from-tag
category: agencies
unpublished: true
---
Properties by tag allows you to manually tag properties and then pull out the properties belonging to that tag in your view:

{% highlight html %}
{% raw %}
<div class="span3">
 {% assign house_property = 'house' | property_from_tag %}
 <a href="{{house_property | url_for_property}}">
  <h4>{{house_property.primary_address_display}}</h4>
  <div class="panel-pic">    
   <img src="{{house_property.photos.first | url_for_property_asset : 'thumb_large' }}" />
  </div>
 </a>
</div>
{% endraw %}
{% endhighlight %}

Be sure to add your tag of choice between the single quotes. Homeflow will make a best attempt at tagging properties based on the information provided in a datafeed. To tag properties in the backend admin, you need to head to the property record and click the Details tab. At the foot of this page you will see the array of tags available. Be aware that your changes may get overwritten by the next datafeed to come in.