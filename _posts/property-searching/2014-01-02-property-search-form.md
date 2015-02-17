---
layout: default
title: Property search form
modal-id: property-search-form
category: property-searching
---
Somewhere in your application layout file you're likely to have a property search form. When the ``Ctesius.Actions.submitSearchForm()`` is called, the system will evaluate every form on the page looking for elements with specified IDs and use them to construct a search.

{% highlight html %}
<form action='/search' id='search' method='get' />
 <input type='hidden' id ='place_id' name='place_id' value='{{place_id}}' />
 <input placeholder='Town or Postcode' type="text" id='location' name="location" value="{{location_field}}"/>
 <input type="radio" name="channel" value="sales" id="buy"> <label>For Sale</label>
 <input type="radio" name="channel" value="lettings" id="let"> <label>To Let</label>
 <select id="type" name='type'>
  <option value="" title="Property type">Property type</option>
  {% raw %}{{ agency | tag_dropdown_list }}{% endraw %}
 </select>
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
 <button onclick="Ctesius.Actions.submitSearchForm(); return false;" type="submit">Search</button>
</form>
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