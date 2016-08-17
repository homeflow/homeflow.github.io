---
layout: default
title: Development plots
modal-id: development-plots
category: property-show-page
---
Development plots work in the same way as normal property show pages and they
have access to all the same property information.

You also have access to the properties child_properties. This returns an array
with any child_properties that are associated with that development. Each child has the following
attributes:

primary_photo_url:
property_id:
property_type:
bathrooms:

#### price
**Returns:** The price of the property as an Integer

#### bedrooms
**Returns:** The property count as an Integer

#### bathrooms
**Returns:** The number of bathrooms as an integer

#### primary_photo_url
**Returns:** The URL path of the primary photo as a String. This will need to be appended to a MrRichard URL.

#### property_id
**Returns:** The Homeflow property_id as an Integer

#### property_type
**Returns:** The name of the type of the property as a String
