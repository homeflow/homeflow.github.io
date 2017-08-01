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
