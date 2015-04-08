---
layout: default
title: Infinite scrolling
modal-id: infinite-scrolling
category: property-results
---
The first step to get up and running is to add a Ctesius ``addConfig`` on your results page within some script tags.

``Ctesius.addConfig('enable_infinite_scroll', true)``

The second step is to wrap your properties results loop in an ``infinite_pages`` ID. In a very basic form:

{% highlight html %}
{% raw %}
<div id="infinite_pages"> 
 <div class="infinite_page">
  <ul>
   {% for property in properties %}
    {% include "properties/property_medium" %}
   {% endfor %}
  </ul>
 </div>
</div>
{% endraw %}
{% endhighlight %}

The next step is define the template and what will be loaded in a new. Note it is wrapped in ``raw`` tags, so the serverside parser will ignore it. Also note that this structure will be a direct copy of the structure within your properties for loop but with the addition of the for loop code and overall structural elements (in this case the unordered list).

{% highlight html %}
{% raw %}{{% endraw %}% raw %{% raw %}}{% endraw %}{% raw %}
 <script id="infinite_scroll_properties_template" type="text/liquid">
  <ul>
   {% for property in properties %}
    <li>
     <a href="{{ property.property_url }}">
      <img src="{{ property.photo }}">
     </a>
     {{ property.status }}
     <a href="{{ property.property_url }}">
      {{ property.price }}
      {{ property.bedrooms }} bedrooms
      {{ property.road_name }}
     </a>       
     <a class="btn-primary" href="{{ property.property_url }}">Full Details</a>
    </li>
   {% endfor %}
  </ul>
 </script>
{% endraw %}{% raw %}{{% endraw %}% endraw %{% raw %}}{% endraw %}
{% endhighlight %}

This in principle should be enough for you to get an output of some description. As always, you might need to tweak the containing elements and CSS as required to get it to format well.

The function also ships with a loading overlay should you want to use it. It is a simple fullscreen fade in and out whilst the properties are being fetched. If you'd rather not have it displayed, you can simply place it far off screen so even when it's triggered it cannot be seen:

``$('.loading').css('left', '9999px')``