---
layout: default
title: The branches index
modal-id: branches-index
category: branches
---
A branches index route would simply be: ``http://www.agency_domain.com/branches``. On our index page we can add the following code:

{% highlight html %}
{% raw %}
{% if branches != empty %}
 {% for branch in branches %}
  {% include "branches/branch_small" %}
 {% endfor %}
{% endif %}
{% endraw %}
{% endhighlight %}

This construct is exactly the same as a properties loop seen before except we are referencing our branches collection as well as including a ``branch_small`` partial for each returned branch. A ``branch_small`` might look something like:

{% highlight html %}
{% raw %}
<div class="branch">
 {% if branch.agency.portal_logo %}
  <img src="{{ branch.agency.portal_logo | url_for_agency_logo : "150!" }}" />
 {% else %}
  <img src="{{ 'awaiting-image.png' | theme_image_url }}" />
 {% endif %}
 <div class="details">
  <h3>
   <a href="{{ branch | url_for_branch}}">{{branch.name}} branch</a>
  </h3>
  <p class="content">
   {{branch.description | strip_tags | truncate : 250}}
  </p>
  <p>
   <a href="{{ branch | url_for_branch}}">More Information</a>
  </p>
 </div>
</div>
{% endraw %}
{% endhighlight %}

#####Map Zoom levels
If you need to manually set the zoom level of the branch map you can do so with the following snippet (replace 15 with any fallback zoom level you wish):

{% highlight html %}
{% raw %}
    Ctesius.addConfig('custom_map_zoom', {% if agency.preferences.google_maps_branch_zoom_level %}{{agency.preferences.google_maps_branch_zoom_level}}{% else %}15{% endif %});
{% endraw %}
{% endhighlight %}