---
layout: default
title: Theme Config.yml
modal-id: theme-config-yml
category: best-practices
---
The ``config.yml`` file in the theme folder is important for defining theme specific options. Below is an example of a ``config.yml`` with some common options:

{% highlight html %}
theme:
  name: "batty"
  type: "agency_theme"
  parent_theme “contador”
  paginations:
    - articles
  default_article_topic: "winkworth"
  search:
    tags:
      - '!archived'
  enabled:
    - branches_by_distance_on_locations
    - searchable_keyword_lookup
    - unbounded_pages
    - no_redirect_on_staff_lead
  site_content_chunks:
    - name: 'my_cool_chunk'
      description: 'A good chunk’
  asset_packs:
   javascript:
    - application.js
   stylesheet:
    - main.lcss
  vendor_assets:
   javascripts:
    - ctesius
    - asset_pack
   stylesheets:
    - asset_pack
{% endhighlight %}    

<br>
