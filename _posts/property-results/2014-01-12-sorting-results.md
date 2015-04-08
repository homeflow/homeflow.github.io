---
layout: default
title: Sorting property results
modal-id: sorting-results
category: property-results
---
You can either use a select box or set of anchors with the fields below to order results. Firstly the HTML with a helper function that gets the current search fragment for us and applies the sort URL:

{% highlight html %}
{% raw %}
<select class="result_sort">
 <option value="most-expensive-first" 
  {% if search.order == 'most-expensive-first' %}selected="selected"{% endif %} 
  data-url="{{ search | search_url_with_sort : 'most-expensive-first' }}">
   Price high &gt; low
 </option>
 <option value="least-expensive-first" 
  {% if search.order == 'least-expensive-first' %}selected="selected"{% endif %} 
  data-url="{{ search | search_url_with_sort : 'least-expensive-first' }}">
   Price low &gt; high
 </option>
 <option value="most-recent-first" 
  {% if search.order == 'most-recent-first' %}selected="selected"{% endif %} 
  data-url="{{ search | search_url_with_sort : 'most-recent-first' }}">
   Most recent first
 </option>
 <option value="most-recently-updated-first" 
  {% if search.order == 'most-recently-updated-first' %}selected="selected"{% endif %} 
  data-url="{{ search | search_url_with_sort : 'most-recently-updated-first' }}">
   Most recently updated first
 </option>
</select>
{% endraw %}
{% endhighlight %}

Next, a small jQuery function is employed to kick the event:

{% highlight javascript %}

$('body').on('change', '.result_sort', function(event) {
 var url = $(':selected', $(event.target)).data('url');
 if(url != undefined) {
  window.location.href = url;
 }
});

{% endhighlight %}