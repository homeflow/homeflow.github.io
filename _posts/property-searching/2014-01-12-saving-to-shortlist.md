---
layout: default
title: Saving to a shortlist
modal-id: saving-to-a-shortlist
category: property-searching
---
A common feature on property websites is saving properties to a semi or permanent storage with the appropriate widgets to link to or add/remove properties as the user sees fit. This kind of function is extremely useful on portals, but is also a nice feature for agencies to have.

Our first port of call is to use our first ``override`` partial so far. An override is simply a partial well-known to Ctesius that's in the ``core`` app ready for use. Sometimes core files can be used without needing to override them but in this instance we'll assume you want to modify the layout or at least have a degree of control over the partial.

In your ``js_templates`` folder, add the partial ``_saved_properties.liquid``. In it we need a couple of constructs, the first is:

{% highlight html %}
{% raw %}
<script id="saved_properties_template" type="text/liquid">
 <div class="content box">
  <h3>My property shortlist</h3>
  <div class="shortlist_inner">
   <div id="property_shortlist" class="content-block">
    <div id='favourite_property_list' class="content"></div>
   </div>
  </div>
 </div>
</script>
{% endraw %}
{% endhighlight %}

Essentially this is our widget container. Here's the next construct:

{% highlight html %}
{% raw %}
<script id="saved_property_template" type="text/liquid">
 <div id="mini_property_{{property.property_id}}" class="mini_property mini_property_{{property.property_id}}">
  <div style="position:relative;" class="clearfix">
   <img src="/liquid_assets/images/delete.png" style="display: none;" id="remove_icon_{{property.property_id}}"
   class="remove_icon" onclick="javascript:Ctesius.Actions.removeSavedProperty({{property.property_id}})">
   <a href="{{property.property_url}}"><img src="{{ property.small_photo }}" class="shortlist_img"></a>
   <div class="featured_property_data">
    <a href="{{property.property_url}}">{{ property.bedrooms }} bedrooms</a><br />
    <a href="{{property.property_url}}">{{ property.price }}</a><br />
    <a href="{{property.property_url}}">{{ property.road_name | truncate : 20 }}</a>
   </div>
  </div>
 </div>
</script>
{% endraw %}
{% endhighlight %}

This construct is the actual saved property record within the widget.

There's quite a lot here to digest but most of it we have touched on previously in the documentation. The ``raw`` tag however, is one we haven't seen so far. Anything within the raw tag is ignored by the Liquid serverside parser. Instead it's sent back to the browser for (in our case) the application JavaScript to process. As you can see we output the property's ID in various places so we can get a handle on it.

Next we need to allow our widget to show up somewhere in your theme - typically a sidebar. Add the following code whereever you would like it to show:

``<div id="saved_properties_view" class="hidden"></div>``.

This will render the results of the script code seen above within the ``saved_properties_view`` div tags.

Next we need to output a save button or link on each property. To do that we add the following code to our ``_property_small.liquid`` that we worked with earlier in the documentation (and the grid view if you have one):

{% highlight html %}
{% raw %}
<a class="shortlist_link_{{ property.property_id }}"
onclick="Ctesius.Actions.addSavedProperty({{property.property_id}}); return false;">
 Add to Shortlist
</a>
{% endraw %}
{% endhighlight %}

The new code here is the ``Ctesius addSavedProperty action`` - essentially this saves the JSON representation of property's information to the browser's local storage for retrieval as and when required. It is now close to working but there's some events we need to add to ``js_event_registers`` to stitch it all together. The first is in an event to do some stuff when the view is rendered (i.e. when the user clicks the add button):

{% highlight html %}
{% raw %}
Ctesius.registerEvent('saved_property_view_rendered', function(saved_property){
 $('#saved_properties_view').removeClass("hidden");
 $(".shortlist_link_"+saved_property.id).html("Remove from Shortlist");
 $(".shortlist_link_"+saved_property.id).attr("onclick", 'Ctesius.Actions.removeSavedProperty('+saved_property.id+'); return false;');
 $('#mini_property_'+saved_property.id).mouseenter(function(){$('#remove_icon_'+saved_property.id).show()});
 $('#mini_property_'+saved_property.id).mouseleave(function(){$('#remove_icon_'+saved_property.id).hide()});
});
{% endraw %}
{% endhighlight %}

Firstly we remove the hidden class from our sidebar widget so it shows. We then target the link, change the HTML to ``Remove from Shortlist`` then we add a click event to remove the very same property. Our last two lines are jQuery callback functions that show or hide the visual aid signifiying the user can remove the property.