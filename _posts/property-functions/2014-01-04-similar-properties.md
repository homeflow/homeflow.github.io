---
layout: default
title: Similar properties
modal-id: similar-properties
category: property-functions
---
At the time of writing the similar properties function can only be used on a property show page. It takes the current property as an argument and calls a helper method called ``similar properties`` which fetches nearby properties that are in a similar price bracket. It is a useful function to pique the user's interest and achieve more property hits in a given session.

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