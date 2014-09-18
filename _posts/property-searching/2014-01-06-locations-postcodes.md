---
layout: default
title: Locations and postcodes
modal-id: locations-and-postcodes
category: property-searching
---
So far we have a basic properties index page and hopefully a set of results using the properties loop. How then, do we deal with locations like counties and towns as well as postcodes? This is where our include partial ``search/_results.liquid`` comes into its own. All we need to do is add three subfolders in the root directory: ``locations``, ``counties`` and ``postcodes``. Within these folders we simply need a ``show.liquid`` file and inside this file we add ``{% raw %}{% include 'search/results' %}{% endraw %}``. This will use our search results partial for the location searches - great. We now need to make sure our page headings reflect the search that has been carried out. We may as well look at pagination whilst we're at it, too...