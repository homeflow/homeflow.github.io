---
layout: default
title: Most recent search template
modal-id: most-recent-search-template
category: property-show-page
---
The most recent search template lives in the same template as the next and previous property template. It is a useful function that gets the search the user carried out to get to the show page. Failing that, it will try and imply a search.

{% highlight html %}
{% raw %}{{% endraw %}% raw %{% raw %}}{% endraw %}{% raw %}
 <script id="most_recent_search_template" type="text/liquid">
  <div class="col-8"><a class="back" href="{{search.link}}">Back to search results </a></div>
 </script>
{% endraw %}{% raw %}{{% endraw %}% endraw %{% raw %}}{% endraw %}
{% endhighlight %}

To output it to your show page, add the following div:

{% highlight html %}
<div id="most_recent_search_view"></div>
{% endhighlight %}