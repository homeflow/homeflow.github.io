---
layout: default
title: Locations and postcodes
modal-id: locations-and-postcodes
category: property-searching
---
All we need to do to deal with locations like counties and towns as well as postcodes is add three subfolders in the root directory: ``locations``, ``counties`` and ``postcodes``. Within these folders we simply need a ``show.liquid`` file and inside this file we add ``include 'search/results'``. This will use our search results partial for the location searches.