---
layout: default
title: Properties from fragment
modal-id: properties-from-fragment
category: agencies
---
Properties from fragment is a function that effectively allows you to run a background search using any search criteria, then loop through the results anywhere on the site using a well defined content block.

If you've been working with search results as well as filtering by price, type and so on, you'll be familiar with the URL 'fragments'. A typical fragment could be: ``from-3-bed/from-200000/up-to-300000``. This is exactly what we can add to the block:

{% highlight html %}
{% raw %}
{% search_from_fragment fragment: status-sold/most-recently-updated-first channel: sales %}
 {% for property in properties limit: 10 %}
  <li>
   <a href="{{ property | url_for_property }}">
    <img src="{{ property.photos.first | url_for_property_asset: "265x160" }}">
    <h5>{{ property.display_address }}</h5>
    <p>{{ property.bedrooms }} bedrooms</p>
   </a>
  </li>
 {% endfor %}
{% endsearch_from_fragment %}
{% endraw %}
{% endhighlight %}
