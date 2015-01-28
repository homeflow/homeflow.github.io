---

layout: default title: Featured properties modal-id: featured-properties

category: property-functions
----------------------------

For an agency, featured properties can play one of two roles depending on what has been set. In your backend admin system, you or the agent can manually feature up to five properties by clicking into the property record, selecting either sales or lettings and selecting the checkbox `Feature on the home page`, which is under the `Status and visibility` section. You can then loop through the properties on your page using the following code construct:

{% highlight liquid %} {% raw %} {% for property in agency.featured_properties limit:2 %} <a href="{{ property | url_for_property }}"> <img src="{{ property.photos.first | url_for_property_asset:"220x215" }}"> {{ property.display_address }} {{ property.price }} </a> {% endfor %} {% endraw %} {% endhighlight %}

If no featured properties have been manually set, the application will call the `recent properties` function instead. This function pulls out five of the latest properties, sorted descending by the date they were created on the Homeflow system.

###Featured properties outside property results pages

Sometimes it is a requirement to have the featured properties on other pages in the site. As the featured properties relies on properties being inluded in the Ctesius Javascript config if is necessary to do this manually.

{% highlight javascript %} {% raw %}<script> $(document).ready(function(){ {% assign properties = agency.featured_properties %} var agency_featured_properties = {% include_as_json properties/properties_list %}.properties Ctesius.addConfig('properties', agency_featured_properties); Ctesius.bootPropertiesCollection(Ctesius.getConfig('properties')); )};</script> {% endraw %} {% endhighlight %}

If you want to 'Add to shortlist' or 'Favourite' these properties then they will need to be added to the
Ctesius config 'properties'. This can be achieved by the placing the following snippet on the page.

{% highlight javascript %}
{% raw %}
<script>
$(window).load(function(){
  Ctesius.appendConfig('properties', {% include_as_json properties/properties_list data: similar_properties target: properties %}.properties);
  Ctesius.bootPropertiesCollection(Ctesius.getConfig('properties'));
  });
</script>
{% endraw %}
{% endhighlight %}
