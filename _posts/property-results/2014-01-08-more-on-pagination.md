---
layout: default
title: More on pagination
modal-id: more-on-pagination
category: property-results
---
Ctesius ships with a ``for pagination`` function. If you've ever used Google before, and let's face it, who hasn't, then you'll be familiar with the pages before and after pagination they utilise at the foot of the search results.

This function takes a couple of arguements: ``previous`` and ``after``.

These arguements allow you to define how many trailing and remaining pages to show. Here's the code:

{% highlight html %}
{% raw %}
{% unless pagination.page_count == 1 %}
 <ul>
  {% if pagination.has_prev_page %}
   {% if pagination.page_count > 2 %}
    <li><a href='{{pagination.first_page_link}}'>&lt; First</a></li>
   {% endif %}
  {% endif %}
  {% for_pagination pagination previous: 4 after : 4 %}
   <li>
    <a href="{% if pagination_item.page_number == pagination.current_page }}#
    {% else %}{{pagination_item.link}}{% endif %}"
    {% if pagination_item.page_number == pagination.current_page %} class='s'{% endif %}>
    {{pagination_item.page_number}}</a>
   </li>
  {% endfor_pagination %}
  {% if pagination.has_next_page and pagination.current_page != pagination.page_count %}
   {% if pagination.page_count > 2 %}
    <li>
     <a href='{{pagination.last_page_link}}'>Last &gt;</a>
    </li>
   {% endif %}
  {% endif %}
 </ul>
{{ endunless }}
{% endraw %}
{% endhighlight %}