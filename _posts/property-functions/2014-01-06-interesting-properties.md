---
layout: default
title: Interesting properties
modal-id: interesting-properties
category: property-functions
---
Our interesting properties algorithm attempts to find properties similar to the ones a user has searched for and/or viewed, then display them in a location such as the home page. Many agency sites have a default output that is replaced if a certain number of interesting properties are returned. The great thing about the interesting properties output is that it works with your normal presentation, so you shouldn't need to rework any of your code.

Our first port of call is to switch on a couple of options in the theme. In your JS Event Registers file add the following:

{% highlight liquid %}
{% raw %}
Ctesius.addConfig('enable_user_history', true);
{% endraw %}
{% endhighlight %}

And if you want to make sure enough properties are on the stack before outputting:

{% highlight liquid %}
{% raw %}
Ctesius.addConfig('minimum_interesting_properties', 1);
{% endraw %}
{% endhighlight %}

Now consider a typical home page presentation:

{% highlight html %}
{% raw %}
<div id='interesting_properties_view'>
 <div class="span3">
  <div class="homePanel box">
   {% for property in agency.recent_sales_properties limit:1 %}
    <a href="{{property | url_for_property}}">
     <h3>New Listings</h3>
     <h4>{{property.primary_address_display}}</h4>
     <img src="{{property.photos.first | url_for_property_asset : 'thumb_large' }}" />
    </a>
   {% endfor %}
  </div>
</div>
</div>
{% endraw %}
{% endhighlight %}

There's nothing special about this - if we had another three you'd have a nice row of recent property boxes. Now, somewhere convenient, we would then add:

{% highlight html %}
{% raw %}
<script id="interesting_properties_template" type="text/liquid">
 <div class="span3">
  <div class="homePanel box">
   {% for property in agency.recent_sales_properties limit:1 %}
    <a href="{{property | url_for_property}}">
     <h3>New Listings</h3>
     <h4>{{property.primary_address_display}}</h4>
     <img src="{{property.photos.first | url_for_property_asset : 'thumb_large' }}" />
    </a>
   {% endfor %}
  </div>
 </div>
</script>
{% endraw %}
{% endhighlight %}

Essentially this is just a copy of the original structure, but within some script tags with the matching ID as seen wrapping the previous code segment: interesting_properties_view. When the app builds up user history, and if it has at least one result, it will replace the block within the ID with the content brought back within the interesting properties template. 

**Important point**: The interesting properties script must be wrapped in raw tags: {% raw %}{%{% endraw %} raw {% raw %}%}{% endraw %} and {% raw %}{%{% endraw %} endraw {% raw %}%}{% endraw %}.