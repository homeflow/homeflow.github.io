---
layout: default
title: Saving searches
modal-id: saving-searches
category: property-searching
---
Saving searches is a tad quicker and easier to set up than the saved properties and they save in much the same way as the saved properties. They also make use of the events system to give the user some feedback. Here's the first bit of code you will need to add where you would like the link/button:

{% highlight html %}
{% raw %}
{% if location %}
 <li><a onclick="Ctesius.Actions.saveCurrentSearch();" id="save_search">SAVE SEARCH</a></li>
{% endif %}
{% endraw %}
{% endhighlight %}

Here you can see we have wrapped the link in a location if statement. You don't _have_ to do this, though a saved search and the resultant email alerts to the user might not be very useful if the properties are not where they want to live or the location where they searched. Much like the saved properties function, here we call ``saveCurrentSearch()``. We also give the link an ID so we can grab it in context using our events.

Speaking of events, here's the two we'll need to provide the user with some feedback:

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

Again we're calling some Ctesius functions that will add or remove the saved search accordingly. We then set the display of the link and add the ``onclick`` events as needed. There's a couple of new statements used in this code that are worth a look:

{% highlight html %}
{% raw %}
$('#saved_searches_link').effect('highlight',{color: '{{theme_preferences.accent_colour}}'}, 3000);
{% endraw %}
{% endhighlight %}

The first is more a concept than anything else - the events that we can get a handle on are not only good for adding and removing properties, searches etc, but can also be used to provide visual aids to the user. Here the ``saved_searches_link`` in the user profile header (more on this later) is highlighted and then fades out to show the user that the search was saved and can be viewed/amended in their control panel.

The other new Liquid tag is ``{% raw %}{{theme_preferences.accent_colour}}{% endraw %}``.

Earlier we mentioned that LCSS files are run through a Liquid filter. If you're building a theme that will be rolled out to multiple agencies, or if you want to standardise the colour palette and manage it in one place, you can use the ``agency/portal admin`` to set the colours, then pull them out in Liquid using tags similar to the one above.