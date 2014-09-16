---
layout: default
title: Branch searching
modal-id: branch-searching
categories: working-with-branches
---
If you're building a portal or larger agency theme, you will pleased to know that users can search for your branches using our geo location database. This comes complete with a handy AJAX style auto suggest location based on the town or city the user enters. To get up and running, first we need to add our form:

{% highlight html %}
{% raw %}
<form action="/branches" id="search" method="get">
 <input type="text" name="location" id="location" class="autocomplete_location">
 <input type='hidden' name='place_id' value='{{place_id}}' class='autocomplete_location_result' />
 <button value="Search" type="submit"></button>
</form>
{% endraw %}
{% endhighlight %}

Next where you branch results need to be, we have:

{% highlight html %}
{% raw %}
{% if branches != empty %}
 {% for branch in branches %}
  {% include 'branches/branch_small' %}
 {% endfor %}
{% else %}
 <h1>Sorry, no branches were found.</h1>
{% endif %}
{% endraw %}
{% endhighlight %}

The output here will be an index of branches, but if we submit our form with a location, our branches controller will go off, fetch the results and display them in place of the index results.