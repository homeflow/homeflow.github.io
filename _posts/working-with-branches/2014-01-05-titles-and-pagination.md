---
layout: default
title: Branch titles and pagination
modal-id: branch-titles-and-pagination
categories: working-with-branches
---
Much like we saw earlier in the documentation with property results, it's useful to output some titles and especially useful to output pagination if the branch results are on several pages. There's a number of ways that you can deal with titles - here's one such example:

{% highlight html %}
{% raw %}
{% if location %}
 {% if location.name != ''%}Branches in {{ location.name }}{% if county %}, {{county.name}}{% endif %}{% endif %}
{% elsif county %}
 Branches in {{ county.name }}
{% elsif postcode %}
 Branches in {{ postcode.postcode }}
{% else %}
 Branches Index
{% endif %}
{% endraw %}
{% endhighlight %}

As you can see, the IF statement checks for the location or location type and outputs the appropriate heading between a heading tag. Remember that if you use the construct multiple times, you can add it to a partial if you wish.

The branches index results comes loaded with the same pagination figures and options we saw in the property results earlier. Here's an example construct:

{% highlight html %}
{% raw %}
Page {{pagination.current_page}} of
{% if pagination.has_next_page %}
 {{pagination.total_count}}
{% else %}
 {{pagination.current_page}}
{% endif %}<br>
{% if pagination.has_prev_page %}
 <a href="{{pagination.previous_page_link}}">&laquo; Previous page</a>
{% endif %}
{% if pagination.has_prev_page and pagination.has_next_page %}
 -
{% endif %}
{% if pagination.has_next_page %}
 <a href="{{pagination.next_page_link}}">Next page &raquo;</a>
{% endif %}
{% endraw %}
{% endhighlight %}

This might output something like:

{% highlight html %}
       Page 2 of 178
« Previous page - Next page »
{% endhighlight %}

By running various IF checks, we can essentially figure out whether there's a next and/or previous page (for example) and format the output accordingly.