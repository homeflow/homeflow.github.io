---
layout: default
title: More on pagination
modal-id: more-on-pagination
categories: property-searching
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

We start with the second ``unless`` statement we've seen. As a reminder, the ``unless`` statement will continue to output the code between the tags unless a certain condition is met. Here if page count is one, then we don't want to try and output the whole for block (incidentally this could be changed to an ``if/else`` and we could output the first page number to signify there's only one page). Next we use a couple of statments we've already seen and a Liquid tag we've not - ``{% raw %}{{pagination.first_page_link}}{% endraw %}`` outputs the first page link.

Next we get into our for loop. First we give it a reference and then ``previous: 4 after : 4``, meaning we want four trailing pages and four forthcoming pages (if they're available). The body of the for loop outputs the appropriate ``li anchor`` code for each. The final block in this code does a couple of checks to make sure there's pages remaining before outputting a helper ``last`` page link. We then close off our if statements and unless statements in the usual way.