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
     <img src="{{property.photo | url_for_property_asset}}" />
    </a>
   {% endfor %}
  </div>
</div>
</div>
{% endraw %}
{% endhighlight %}

There's nothing special about this - if we had another three you'd have a nice row of recent property boxes. Now, somewhere convenient, we would then add:

{% highlight html %}
{% raw %}{%{% endraw %} raw {% raw %}%}{% endraw %}
{% raw %}
  <script id="interesting_properties_template" type="text/liquid">
   <div class="span3">
    <div class="homePanel box">
     {% for property in properties limit:1 %}
      <a href="{{property.property_url | url_for_property}}">
       <h3>New Listings</h3>
       <h4>{{property.primary_address_display}}</h4>
       <img src="{{property.photo | url_for_property_asset}}" />
      </a>
     {% endfor %}
    </div>
   </div>
  </script>
{% endraw %}
{% raw %}{%{% endraw %} endraw {% raw %}%}{% endraw %}
{% endhighlight %}

Essentially this is just a copy of the original structure, but with some raw tags (the Liquid serverside parser ignores code incased in raw tags) and some script tags with the matching ID as seen wrapping the previous code segment: interesting_properties_view. When the app builds up user history, and if it has at least one result, it will replace the block within the ID with the content brought back within the interesting properties template. Also note that a couple of fields are different - we use ``for property in properties`` in the for loop and ``property.property_url`` to get the property's URL.

###Working with statuses and property fields

At the time of writing, the property status Liquid that finds and outputs the appropriate sash is not available for use on the Interesting Properties output. Instead, the solution is to add the property's channel to the ``properties_list.ljson``, then run some Liquid checks to output the appropriate sash.

``status: "{% raw %}{{property.status}}{% endraw %}"`` - add to the LJSON<br>
``primary_channel: "{% raw %}{{property.primary_channel}}{% endraw %}"`` - also worth adding to get the channel

{% highlight liquid %}
{% raw %}
{% if property.primary_channel == 'sales' %}
 {% if property.status == 'SSTC' }
  <img src="{{ 'sstc.jpg' | theme_image_url }}" class="property-status" />
 {% endif %}
{% endif %}
{% endraw %}
{% endhighlight %}

Most fields can be added to the JSON, so if you wanted to output ``property.town`` for example, you could add it to the JSON then check and output put it to the Interesting Properties view.

###Working with User History

A handy event and callback is available to you as and when the user history for the Interesting Properties output is built up. This can be used to add a custom title, background or anything else you please.

{% highlight javascript %}
{% raw %}
Ctesius.registerEvent('user_history_ready', function(collection){
 var last_search = collection.last()

 if (last_search != undefined && last_search.get('place') != undefined){
  var place = last_search.get('place').get('name')
 }

 console.log(last_search)
 console.log(place)
});  
{% endraw %}
{% endhighlight %}

In this code sample you could run a test on place, then use a jQuery attribute change on an element.