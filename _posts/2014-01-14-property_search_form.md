---
layout: default
title: Constructing a property search form
modal-id: constructing-a-property-search-form
---
Somewhere in your application layout file you're likely to have a property search form. There are a myriad of filter options you can show and a couple of methods of searching which we'll explore later, but for now is a basic form is below. Note we have stripped any classes or styling to keep it as simple as possible:

{% highlight html %}
<form action='/search' id='search' method='get' />
 <input type="radio" name="channel" value="sales" id="buy"> <label>For Sale</label>
 <input type="radio" name="channel" value="lettings" id="let"> <label>To Let</label>
 <button onclick="Ctesius.Actions.submitSearchForm(); return false;" type="submit">Search</button>
</form>
{% endhighlight %}

When the ``Ctesius.Actions.submitSearchForm()`` is called the system will evaluate every form on the page looking for elements with specified IDs and use them to construct a search. Here the only fields the user can select are whether it's a sales or lettings search. The results that will be shown with this type of form will be an ``index`` of an agency or portal's properties - this is where our ``/properties/index.liquid`` file comes in. More on that in the [Displaying search results](#displaying-search-results) section.

Expanding on our first example, we can now add two addition fields that allow the user to type in a location. If it's recognised in our database, we'll load a number of suggested locations for the user to select. The hidden place ID field is a lookup reference for our system and is required in the source. With just two extra fields your property search will be completely supported by our geo location database:

{% highlight html %}
{% raw %}
<input type='hidden' id ='place_id' name='place_id' value='{{place_id}}' />
<input placeholder='Town or Postcode' type="text" id='location' name="location" value="{{location_field}}"/>
{% endraw %}
{% endhighlight %}

Now let's add some beds and price bracket options:

{% highlight html %}
<select id="min_beds" name='min_beds'>
 <option value="" title="Min beds">Beds min</option>
 <option value="1" title="1 Bed">1 bed</option>
 <option value="2" title="2 Beds">2 beds</option>
</select>
<select id="max_beds" name='max_beds'>
 <option value="" title="Max beds">Beds max</option>
 <option value="1" title="1 Bed">1 bed</option>
 <option value="2" title="2 Beds">2 beds</option>
</select>
<select id="min_price" name='min_price'>
 <option value="" title="Min price">Price min</option>
</select>
<select id="max_price" name='max_price'>
 <option value="" title="Max price">Price max</option>
</select>
{% endhighlight %}

This is probably all self-explanatory. One thing to note is that the IDs and names are important so we can process the form.

Finally let's add a property type selector:

{% highlight html %}
{% raw %}
<select id="type" name='type'>
 <option value="" title="Property type">Property type</option>
 {{ agency | tag_dropdown_list }}
</select>
{% endraw %}
{% endhighlight %}

You will note a snippet of Liquid here. This code takes some pre-selected types in the Agency or Portal Admin and outputs them as options.

If it were a portal, you would use the portal tag instead:

``{% raw %}{{ portal | tag_dropdown_list }}{% endraw %}``

Another option is to simply specify the types - the names here must match what we use as type references:

{% highlight html %}
<option value="cottage" title="cottage">Cottage</option>
<option value="farmhouse" title="farmhouse">Farmhouse</option>
<option value="townhouse" title="townhouse">Townhouse</option>
{% endhighlight %}

Again you can style the form and position it in anyway you choose. Let's move on and see how we deal with property search results. Just before that though, we'll show you how you can disambiguate a user's search as well as provide a handy helper template.