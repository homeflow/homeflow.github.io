---
layout: default
title: Hestia URLs
"modal-id": "hestia-urls"
category: appendix
published: true
---


Hestia serves up information to the Ctesius app in JSON format. There are a number of well defined URLs you can use to access this data via the browser:

#### Properties
http://index1.homeflow.co.uk/properties/4631183?api_key=XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX

#### Agencies
http://index1.homeflow.co.uk/agencies/9700/?api_key=XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX

#### Branches
http://index1.homeflow.co.uk/branches/18380?api_key=XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX

#### CMS Pages
http://index1.homeflow.co.uk/sites/401/pages/about-us?api_key=XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX

#### Places/locations
http://index1.homeflow.co.uk/places?api_key=XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX&search[name]=elstead

#### Nodes
http://index1.homeflow.co.uk/sites/{:site_id}/nodes/?api_key=XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX
http://index1.homeflow.co.uk/sites/{:site_id}/nodes/{:node_id}?api_key=XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX

For staff, see the agencies Hestia URL.

If you are building a standalone app you can use the Homeflow API Gem. Click [here](http://developer.homeflow.co.uk/homeflow-api-gem/) for info.
