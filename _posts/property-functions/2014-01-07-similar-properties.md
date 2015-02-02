---
layout: default
title: Similar properties
modal-id: similar-properties
category: property-functions
---
At the time of writing the similar properties function is generally used on a property show page. It takes the current property as an argument and calls a helper method called ``similar properties`` which fetches nearby properties that are in a similar price bracket. It is a useful function to pique the user's interest and achieve more property hits in a given session.

{% highlight liquid %}
{% raw %}
{% assign similar_properties = property | similar_properties %}
{% if similar_properties.first %}
 <h2>Similar properties</h2>
 {% for property in similar_properties limit: 2 %}
  {% include 'properties/property_small' %}
 {% endfor %}
{% endif %}
{% endraw %}
{% endhighlight %}

Similar to the featured properties seen before, if you would like to utilise the shortlist function on the similar properties output, we need to add a snippet of JavaScript to the page:

{% highlight javascript %}
{% raw %}
$(document).ready(function(){
 Ctesius.appendConfig('properties', {% include_as_json properties/properties_list
 data: similar_properties target: properties %}.properties);
 Ctesius.bootPropertiesCollection(Ctesius.getConfig('properties'));
});
{% endraw %}
{% endhighlight %}