---
layout: default
title: The agency show page
modal-id: agency-show-page
categories: working-with-agencies
---
Anything agency related will reside in the ``agencies`` folder in your Rails directory structure and your show page will follow the normal format of ``show.liquid``. Let's start to build the page using the agency name, agency description and the agency's portal logo with a fallback to their default logo:

{% highlight html %}
{% raw %}
<h1>{{agency.name}}</h1>
{% endraw %}
{% endhighlight %}

{% highlight html %}
{% raw %}
{% if agency.portal_logo %}
 <img src="{{agency.portal_logo | url_for_agency_logo : "200x_"}}" />
{% elsif agency.logo %}
 <img src="{{agency.logo | url_for_agency_logo : "200x_"}}" />
{% endif %}
{% endraw %}
{% endhighlight %}

``{% raw %}{{agency.description}}{% endraw %}``

Next, let's add a Google style map to our show page - note that this will show the branches belonging to an agency:

{% highlight html %}
<div id='agency_map'></div>
{% endhighlight %}

{% highlight html %}
{% raw %}
<script>
 {{ gmap_for agency.branches as roadmap in agency_map }}
</script>
{% endraw %}
{% endhighlight %}

Don't forget to give your map div a height and a width setting in your CSS.

If you would prefer to use a Leaflet style map:

{% highlight html %}
<div id='branches_map'></div>
{% endhighlight %}

{% highlight html %}
{% raw %}
<script type="text/javascript">
 Ctesius.addConfig('branch_map_element', 'branches_map');
 Ctesius.addConfig('branches', {{ include_as_json branches/branches_list }});
</script>
{% endraw %}
{% endhighlight %}

Now let's extract the branches of an agency, including their branch pic or logo, description etc:

{% highlight html %}
{% raw %}
{% for branch in agency.branches_ordered_alphanumerically %}
 {% include "branches/branch_small" %}
{% endfor %}
{% endraw %}
{% endhighlight %}

Note that we're ordering the branches alphabetically using a helper function and we're reusing our ``branch_small``. Not only is this excellent reuse, but it means if your branch_small layout is sorted, it should work out of the box on you agencies pages. In addition, when you need to make a change to it, it will be reflected on all pages that use it.

Finally, let's see how we can extract some social media links from the CRM:

{% highlight html %}
{% raw %}
{% if agency.has_social_links %}
 <div class="agency_social">
  {% if agency.facebook_uri %}
   <a href="{{agency.facebook_uri }}" target="_blank"><img src="{{'facebook' | theme_image_url}}" width="32" height="32"></a>
  {% endif %}
  {% if agency.twitter_uri %}
   <a href="{{agency.twitter_uri }}" target="_blank"><img src="{{'twitter' | theme_image_url}}" width="32" height="32"></a>
  {% endif %}
  {% if agency.linkedin_uri %}
   <a href="{{agency.linkedin_uri }}" target="_blank"><img src="{{'linkedin' | theme_image_url}}" width="32" height="32"></a>
  {% endif %}
  {% if agency.googleplus_uri %}
   <a href="{{agency.googleplus_uri }}" target="_blank"><img src="{{'google-plus' | theme_image_url}}" width="32" height="32"></a>
  {% endif %}
 </div>
{% endif %}
{% endraw %}
{% endhighlight %}

This block of code first executes a ``has_social_links`` function - this checks whether any one of the standard social media slots has a value. If at least one does, it will execute the block. We then use individual agency drop checks to see if the URI is available and output a theme image linking to the URI if so.