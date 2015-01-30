---
layout: default
title: Config YAML
modal-id: config-yaml
category: theme-config-options
---
As we've touched upon in other parts of the documentation, the ``config.yml`` file can be looked on as a central configuration repository for your theme. There are a number of options that you can add that will effect the way your theme works. YAML files are sensitive to spaces and tabbing and have a tree like format in regard to sections, keys and values. If you add some new values and get an error straight after, you may have formatted it incorrectly.

Below is a growing list of options you can use:

####name: 'name'
**Purpose:** the name of your theme

####cache_for: 'value'
**Purpose:** caching

####type: 'agency_theme'
**Purpose:** the type of theme (normally added for you)

####enabled:
**Purpose:** a container of global options that can include:

####enabled: > 'national_search'
**Purpose:** enables national searching

####enabled: > 'include_count_on_global_listings' (deprecated)
**Purpose:** total count of properties in a result set made available (now enabled by default)

####enabled: > - 'branches_by_distance_on_locations'
**Purpose:**

####enabled: > - 'disambiguation'
**Purpose:** enables national searching

####enabled: > - 'searchable_keyword_lookup'
**Purpose:**

####sidebars:
**Purpose:** a collection of controller/action sidebars to render

####sidebars: > 'controller#action' : 'sidebar_to_render'
**Purpose:** declaration of sidebar

####site_content_chunks:
**Purpose**: chunks defined here will show up in the agent's CMS admin as available them chunks

####site_content_chunks: > - name: 'name of chunk'
**Purpose:** name of the chunk

####site_content_chunks: > description: 'description'
**Purpose:**  role of the chunk

####category_assignments:
**Purpose:**  assign categories to pages for general purposes

####asset_packs:
**Purpose:**  container for JS and CSS asset packs

####asset_packs: > javascript:
**Purpose:**  container for JS asset packs

####asset_packs: > javascript: > - javascript_file_name
**Purpose:**  a record for one JS file to minify

####asset_packs: > stylesheet:
**Purpose:**  container for CSS asset packs

####asset_packs: > stylesheet: > - css_file_name
**Purpose:**  a record for one CSS file to minify (add .css extension for none LCSS files)
