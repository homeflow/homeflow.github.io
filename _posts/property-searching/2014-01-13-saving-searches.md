---
layout: default
title: Saving searches
modal-id: saving-searches
category: property-searching
---
Here's the first bit of code you will need to add where you would like the save search link/button:

{% highlight html %}
{% raw %}
{% if location %}
 <li><a onclick="Ctesius.Actions.saveCurrentSearch();" id="save_search">SAVE SEARCH</a></li>
{% endif %}
{% endraw %}
{% endhighlight %}

Then there's two events we need to provide the user with some feedback:

{% highlight html %}
{% raw %}
Ctesius.registerEvent('saved_search_added', function(search, collection){
 if (search.equalTo(Ctesius.getSearch())){
  $('#save_search').html('REMOVE SEARCH');
  $("#save_search").attr("onClick", 'Ctesius.Actions.removeSavedSearch("'+search.search_id()+'");')
 }

 $('#saved_searches_link').effect('highlight',{color: '{{theme_preferences.accent_colour}}'}, 3000);
});

Ctesius.registerEvent('saved_search_removed', function(search, collection){
 if (search.equalTo(Ctesius.getSearch())){
  $("#save_search").html("SAVE SEARCH")
  $("#save_search").attr("onclick", 'Ctesius.Actions.saveCurrentSearch();')
 }
});
{% endraw %}
{% endhighlight %}