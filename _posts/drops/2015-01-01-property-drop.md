---
layout: default
title: Property Drop
modal-id: property-drop
category: drops
---

*Updated 2/2/2017*

**NOTE:** You should always check that a variable exists before you try to use it, to avoid errors when the value is nil.
e.g.
{% highlight html %}
{% raw %}
{% if property.video_url %}
  {% property.video_url | split: '/' %}
{% endif %}
{% endraw %}
{% endhighlight %}

#### audiotour_url
**Returns:** The url for the property's audio tour as a string, if it has one.

#### acreage
**Returns:** The total acreage of the property, as an integer.

#### acreage_float
**Returns:** The total acreage of the property, as a float.

#### address_with_commas
*Returns:** The full property address as a string, with the lines separated by commas.

#### associated_profile
*Returns:** A random staff member from those associated with the property.

#### associated_profiles
*Returns:** An array of staff members associated with the property.

#### associated_profiles_with_avatar
*Returns:** An array of staff members associated with the property who have avatar images.

#### associated_profile_with_avatar
**Returns:** A random staff member from those associated with the property who have avatar images.

#### associated_sales_profile
*Returns:** A random staff member from those associated with the property who are contactable for sales.

#### associated_sales_profiles
*Returns:** An array of staff members associated with the property who are contactable for sales.

#### associated_lettings_profile
*Returns:** A random staff member from those associated with the property who are contactable for lettings.

#### associated_lettings_profiles
*Returns:** An array of staff members associated with the property who are contactable for lettings.

#### available_on
**Returns:** If supplied, the date the property is available.

#### bathrooms
**Returns:** An integer for number of bathrooms that sometimes comes in as zero or empty so needs to be checked.

#### branch
**Returns:** Return the associated branch for the property as a BranchDrop.

### branch_name
**Returns:** the name of the associated branch as a string.

### branch_url_label
**Returns:** the associated branch's url label (the last part of the url for linking to a branch).

### branch_id
**Returns:** the associated branch's ID.

#### bedrooms
**Returns:** An integer for bedroom count that sometimes comes in as zero or empty so needs to be checked.

### bedrooms_text
**Returns:** A string of the number of bedrooms followed by the correctly pluralized word. e.g "1 bedroom" / "2 bedrooms"

#### brochures
**Returns:** This for loop would output all the brochures supplied.<br/>
**Example use:**
{% highlight html %}
{% raw %}
{% for brochure in property.brochures %}
 <li><a href="{{ brochure | url_for_property_asset }}">Download brochure</a></li>
{% endfor %}
{% endraw %}
{% endhighlight %}

#### building_name
**Returns:** The name of the property's building, if it has one.

#### child_properties
**Returns:** the property's child properties, if it has any.

#### county
**Returns:** The property's county.

#### days_on_market
**Returns:** The number of days the property has been available.

#### description
**Returns:** The property's full description (short + long if the short description is not taken from the long description).

#### epc_charts
**Returns:** This for loop would output all the EPC charts supplied.<br/>
**Example use:**
{% highlight html %}
{% raw %}
{% for epc_chart in property.epc_charts %}
 {% if forloop.first %}
  <a href="{{ epc_chart | url_for_property_asset }}">
  {% if property.epc_charts.size == 1 %}
   View EPC chart
  {% else %}
   View EPC charts
  {% endif %}
  </a>
 {% else %}
  <a href="{{ epc_chart | url_for_property_asset }}" style="display:none"></a>
 {% endif %}
{% endfor %}
{% endraw %}
{% endhighlight %}

#### external_url
**Returns:** the url for the property's first external link.

#### features
**Returns:** A list of property features that can be displayed as bullet points.

#### floorplans
**Returns:** The collection of floor plans. This loop could output the floor plans to a light box e.g Fancybox, Colorbox, etc.<br/>
**Example use:**
{% highlight html %}
{% raw %}
{% for floorplan in property.floorplans %}
 {% if forloop.first %}
  <a href="http://mr0.homeflow.co.uk/{{ floorplan.image }}" title="Floor plan">
  {% if property.floorplans.size == 1 %}
    View floor plan
   {% else %}
    View floor plans
  {% endif %}
  </a>
  {% else %}
   <a href="http://mr0.homeflow.co.uk/{{ floorplan.image }}" style="display:none;" title="Floor plan"></a>
 {% endif %}
{% endfor %}
{% endraw %}
{% endhighlight %}

#### has_audio_tour?
**Returns:** A boolean value for whether the property has an audio tour.

#### has_external?
**Returns:** A boolean value for whether the property has an external link.

#### has_video?
**Returns:** A boolean value for whether the property has a video.

#### has_virtual_tour?
**Returns:** A boolean value for whether the property has a virtual tour.

#### high_res_photos
**Returns:** an array of high resolution photos for the property, if available.

#### home_reports
**Returns:** An array of home reports for the property, if there are any.

#### image_only_epc_charts
**Returns:** EPC charts that are images.

#### investment_yield
**Returns:** The investment yield for the property, if available (defaults to 0).

#### is_auction?
**Returns a boolean value for whether the property's tags contains 'auction'

#### is_commercial?
**Returns:** a boolean value for whether the property's tags contains 'commercial'

#### is_new_homes?
**Returns a boolean value for whether the property's tags contains 'new homes'

#### is_short_let?
**Returns:** A Boolean if the property is a short let property

#### is_premium?
**Returns a boolean value for whether the property's tags contains 'premium'

#### lettings_fee_text
**Returns:** The body of a content chunk named 'lettings_fee_text' if it exists and the property's primary channel is lettings.

#### links
Any links for the property.

#### long_description
**Returns:** the long description for the property.

#### mab_typical_repayments
**Returns:** the typical repayment according to the mortgage advice bureau.

#### main_photo
**Returns:** the property's first photo.

#### nearest_location
**Returns:** the property's nearest location, as a [LocationDrop](/drops/location-drop.html).

### nodes
**Returns:** The nodes for the property, if there are any.

#### photos
**Returns:** an array of the photos for the property.

#### price
**Returns:** the property's price.

#### price_without_qualifier
**Returns:** the property's price without the '£' or any preceding qualified like 'Offers in the region of'.

#### property_primary_channel
**Returns:** 'sales' or 'lettings'

#### property_ref
**Returns:** The agent's supplied property reference.

#### raw_description
**Returns:** The property's description, with any HTML tags stripped out.

#### raw_short_description
**Returns:** The property's short description, with any HTML tags stripped out.

#### reception_rooms
**Returns:** A numerical figure that sometimes comes in as zero or empty so needs to be checked.

### rent_pw_value
**Returns:** The property's rent calculated for one week.

#### road_name
**Returns:** The property's road name.

#### short_description
**Returns:** a short description for the property, if it has one.

#### short_or_long_description
**Returns:** The short description, if it has one. Otherwise, the long description.

#### square_feet
**Returns:** The total area of the property, in square feet.

#### tags
**Returns:** An array of the tags set for the property.

#### url_description
A slug for the property - using bedrooms, type, road name and postcode and joined with hyphens.

#### vox_number
**Returns:** Homeflow is able to generate recorded telephone numbers for properties. Doing a check on this drop can see whether one is available.

#### video_url
**Returns:** The url for the property's first video, if it has one (as a string).

#### virtual_tour_url
**Returns:** the url for the property's virtual tour, if it has one (as a string).
