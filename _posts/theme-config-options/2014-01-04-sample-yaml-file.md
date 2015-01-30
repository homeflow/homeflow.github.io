---
layout: default
title: Sample YAML file
modal-id: sample-yaml-file
category: theme-config-options
---

Here's a sample theme YAML file:

{% highlight yaml %}
{% raw %}
theme:
  name: "Hatch"
  cache_for: 5
  type: "agency_theme"
  enabled: 
    - "national_search"
    - 'include_count_on_global_listings'
  sidebars:
    'branches#show' : 'branch_show_sidebar'
    'branches#index' : 'branch_show_sidebar'
    'branches#properties' : 'property_search_sidebar'
    'properties#index' : 'property_search_sidebar'
    'locations#show' : 'property_search_sidebar'
    'staff#show' : 'staff_show_sidebar'
    'home#home' : 'home_home_sidebar'
    'users#new' : 'users_new_sidebar'
  site_content_chunks:
    - name: 'sales_channel_sidebar_ad_unit'
      description: 'The ad unit for your sales sidebar section'
    - name: 'branches_list'
      description: 'top branches list'
  category_assignments:
    'pages#request_valuation' : 'about'
  asset_packs:
    javascript:
      - respond
      - vendor/jquery.mobile.custom.min
      - vendor/bxslider/jquery.bxslider.min
      - vendor/jquery.scrollTo.min
      - vendor/jquery.tooltipster.min
    stylesheet:
      - normalize.min.css
      - dropkick.css
      - main.lcss
      - tooltipster.css
      - leaflet
{% endraw %}
{% endhighlight %}