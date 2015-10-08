---
layout: default
title: Location guide pages
modal-id: location-guide-pages
category: location-guides
---
A route exists in the Ctesius app to location guide pages, this means you can begin to build up content for individual locations. The route for this page is:

{% highlight html %}
/location_guides/:location
{% endhighlight %}

Within your theme, you will need to add a ``location_guides`` folder and within it, a ``show.liquid`` file. This file will contain all of the node blocks you require to pull out content chunks, branch information, properties and so on. 

For instance, if a branch served the town of 'Tamworth', you might create a Tamworth node, with the slug 'tamworth'. You could then get to it using ``/location_guides/tamworth``.