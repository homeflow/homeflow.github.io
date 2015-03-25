---
layout: default
title: Headings and pagination
modal-id: headings-and-pagination
category: property-results
---
Headings need to reflect the search the user has carried out or it should output a very general statement if it's an index search.

{% highlight html %}
{% raw %}
<h1>
 {{search.dictionary.general_collective | capitalize}}
 {{search.dictionary.preposition}}
 {% if location %}in {{location.name}}{% endif %}
</h1>
{% endraw %}
{% endhighlight %}

This could output something like:

{% highlight html %}
Houses for sale in Walton on Thames
{% endhighlight %}

The ``general_collective`` is the property type, the ``preposition`` is the channel (sales or lettings) and finally we do a ``location`` test and output the ``in`` and ``{% raw %}{{location.name}}{% endraw %}`` if it comes back as true. Let's look at another example:

{% highlight html %}
{% raw %}
{{pagination.from_record}} to {{pagination.to_record}} of {{pagination.total_count}}
Properties found
{% if location %}
 in {{location.name}}
{% endif %}
{% if pagination.has_prev_page %}
    | <a href="{{pagination.previous_page_link}}" class="pagination_prev">
    Previous {{pagination.page_size}}
   </a>
{% endif %}
{% if pagination.has_next_page %}
    | <a href="{{pagination.next_page_link}}" class="pagination_next">
    Next {{pagination.page_size}}
  </a>
{% endif %}
{% endraw %}
{% endhighlight %}

This might output something like:

``1 to 12 of 31 Properties found in Walton on Thames | Next 12``