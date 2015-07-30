---
layout: default
title: Next and previous properties
modal-id: next-and-previous-properties
category: property-show-page
---
The next and previous property functions allow the user to cycle through a set of search results, either using the search the user performed to get to the show page, or implying the search based on the details of the property the user is on.

To get up and running, add a partial template under ``js_templates`` called ``_next_prev_recent_search.liquid`` and include in appplication.liquid. In it, add and modify the following template:

{% highlight html %}
{% raw %}{{% endraw %}% raw %{% raw %}}{% endraw %}{% raw %}
 <script id="next_and_previous_property_template" type="text/liquid">
  <div class="col-4">
   {% if previous_property %}
    <a class="previous-prop" href="{{ previous_property.property_url }}">Previous Property</a> 
   {% endif %}
   {% if next_property %}
    <a class="next-prop" href="{{ next_property.property_url }}">Next property</a>
   {% endif %}
  </div>
 </script>
{% endraw %}{% raw %}{{% endraw %}% endraw %{% raw %}}{% endraw %}
{% endhighlight %}

Then on your property show page, wherever you want the template to render, add:

{% highlight html %}
<div id="next_and_previous_property_view"></div>
{% endhighlight %}

You will need to turn the supporting functionality in your theme by adding the following Ctesius config setting (as with other features).

{% highlight html %}
Ctesius.addConfig('enable_user_history', true);
{% endhighlight %}