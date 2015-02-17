---
layout: default
title: Search Disambiguation
modal-id: search-disambiguation
category: property-searching
---
If the user does not select a particular result from the auto suggest, Ctesius will send to the user to the page as if they selected the top result. Whilst this may be fine most of the time, you might want to ask your user to 'fine tune' their results by picking one of the alternative locations that were found.

To add this functionality, we first add a 'disambiguation' line to your theme's YAML file:

{% highlight yaml %}
  enabled:
    - "national_search"
    - "global_branch_search"
    - "branches_by_distance_on_locations"
    - "disambiguation"
{% endhighlight %}

This will cause a search with the query 'Brighton' to append ``#/disambiguate/brighton`` to the search result page. Ctesius will then perform a place search and render the provided view. The contents of this view can be added to an include or could be added to your theme's source in an appropriate place. 

Ctesius will automatically render the contents of template into the view but will replace the tags with the returned content. Note that in order for Ctesius to do this, the entire script and view must be wrapped in raw tags so that the serverside parser doesn't try and render the tags.

{% highlight html %}

{% raw %}{{% endraw %}% raw %{% raw %}}{% endraw %}{% raw %}
 <script id='disambiguation_template' type='text/liquid'>
   <p>Did you mean:</p>
   {% for place in places limit: 3 %}
     <p><a href='{{place.url}}'>{{place.name}}</a></p>
   {% endfor %}
 </script>
{% endraw %}{% raw %}{{% endraw %}% endraw %{% raw %}}{% endraw %}

<div id='disambiguation_view'></div>

{% endhighlight %}