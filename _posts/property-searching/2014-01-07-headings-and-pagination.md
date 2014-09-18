---
layout: default
title: Headings and pagination
modal-id: headings-and-pagination
category: property-searching
---
Headings need to reflect the search the user has carried out or it should output a very general statement if it's an index search. There's other considerations here; for instance if it is a county or postcode seach and so on. Some developers choose to add pagination statistics and pagination navigation together with search and location information, whereas others choose to seperate the two - you are free to find whatever suits you/your client. Note that the code below could be in  ``search/_results.liquid`` - another logical place would be ``properties/_results.liquid``. Here's an example heading:

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

This example starts with the ``from_record`` - if your page size is ten (which is the default) then this will go ``1``, ``11``, ``21`` etc. We then output the ``to_record``, which again, if we're going up in tens, this would be ``10``, ``20``, ``30`` etc. We then output ``{% raw %}{{pagination.total_count}}{% endraw %}``, which outputs the item count.

Our next segment of code is two if statements that will output next and previous buttons or links if they are required. As you can see, we can get the next and previous links using the appropriate Liquid syntax as well as a handle on the page size, which is most likely going to be ten, but could be twelve, fourteen or whatever you or your client requires.