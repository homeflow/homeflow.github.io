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

Next, we'll add a `properties/_properties_list.ljson` file to the project. This file is used by the server to render the properties as liquid objects, along with any variables we define:

{% highlight liquid %}
{% raw %}
properties :
{% for property in properties %}
  -
    photo : {{ property.main_photo | url_for_property_photo : "300x185" }}
    property_url : {{ property | url_for_property }}
    short_description : {{ property.short_description | truncate : 150 | capitalize | yaml_safe}}
    display_address : {{property.display_address | truncate: 90 | yaml_safe}}
    price : {{ property.price }}
    bedrooms: {{property.bedrooms | yaml_safe }}
    property_id: {{property.property_id}}
    status: {{ property.status }}
    primary_channel: {{property.primary_channel}}
{% endfor %}
pagination :
    current_page : {{ pagination.current_page }}
    has_prev_page : {{ pagination.has_prev_page }}
    total_count : {{ pagination.total_count }}
    has_next_page : {{ pagination.has_next_page }}
    from_record : {{ pagination.from_record }}
    to_record : {{ pagination.to_record}}
{% endraw %}
{% endhighlight %}

You can see a comprehensive list of the available variables for a property [here](/drops/property-drop.html).

Now we can define a template that will be used by each infinite scroll page. As with all HTML template script elements, this can be placed anywhere as long as it's available somewhere in the DOM on the page where it needs to be rendered. This template can make use of the variables we defined inside the `_properties_list.ljson` file:

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
     </a>
     <a class="btn-primary" href="{{ property.property_url }}">Full Details</a>
    </li>
   {% endfor %}
  </ul>
 </script>
{% endraw %}{% raw %}{{% endraw %}% endraw %{% raw %}}{% endraw %}
{% endhighlight %}

Note that the template is wrapped in ``raw`` tags, so the serverside parser will ignore it. The consequence of this is that **you cannot use complex liquid statements, includes for partials or JavaScript inside it**. This means that things like liquid filters should be used inside the ljson file, where variables are defined. Also note that this structure will be a direct copy of the structure within your properties for loop.

This should be enough to get the infinite scroll working on your property index page. As always, you might need to tweak the containing elements and CSS as required to get it to format well.
