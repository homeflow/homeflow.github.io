---
layout: default
title: Property Facets Drop
modal-id: property-facets-drop
category: drops
---

To access the additional information about the property, just reference property.facets, e.g.

{% highlight html %}
{% raw %}
{{ property.facets.council_tax_amount }}
{% endraw %}
{% endhighlight %}

These are the available values:

#### council_tax_amount
**Returns:** The cost of the property's council tax.

#### council_tax_band
**Returns:** The single-letter designation for the property's council tax band.

#### local_authority
**Returns:** The property's local council, e.g. "London Borough of Brent"

#### attr_chain_free
**Returns:** a 1 if the property is chain-free.

#### co2_actual_rating
**Returns:** the actual CO2 rating for the property.

#### co2_potential_rating
**Returns:** the potential CO2 rating for the property.

#### epc_actual_rating
**Returns:** the actual EPC rating for the property.

#### landlord_reg_number
**Returns:** the landlord registration number, if applicable.

#### heating_type
**Returns:** the type of heating for the property.

#### accepted_occupancy_couple
**Returns:** a 1 if couples occupancy is accepted.

#### accepted_occupancy_single
**Returns:** a 1 if single occupancy is accepted.

#### attr_studio
**Returns:** a 1 if the property is a studio.

#### let_duration_max
**Returns:** the maximum let duration.

#### rent_includes_rates_tax
**Returns:** a 1 if the rent includes rates tax.
