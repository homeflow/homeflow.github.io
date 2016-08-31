---
layout: default
title: Agency Drop
modal-id: agency-drop
category: drops
---

Below are the methods available on the AgencyDrop, what they return and also what they expect to be passed when calling the method.

#### address_html
**Returns:** Agency address with HTML formatting

#### agency_portal_preferences
**Returns:** A collection of agency_portal_prefereces. See AgencyPortalPreferenceDrop

#### articles
**Returns:** An array of all articles for an Agency. See ArticleDrop

#### article(article_id)
**Returns:** See ArticleDrop<br/>
**Expects:** An article_id as a string

#### article_topics
**Returns:** All the topics used by the Agency for articles. Useful for blog type topic lists

#### article_topics_after_exclusion
**Returns:** An array of topics

#### banners
**Returns:** An array of banners set up by an Agency

#### banner(banner_id)
**Returns:** The specified BannerDrop<br/>
**Expects:** A banner_id as a string

#### branch_by_id
**Returns:** A BranchDrop object<br/>
**Expects:** A branch_id as a string

#### branches
**Returns:** A collection of all the Agency branches

#### carousel_items
**Returns:** A collection of the Agency's CarouselItemDrop's

#### default_search_channel
**Returns:** The default search channel for the Agency, either 'sales' or 'lettings'

#### display_agency_logo_for_national_search

#### facebook_uri
**Returns:** A string URL for the Agency's facebook page

#### featured_pages
**Returns:** A collection of PageDrop's that have been set to be featured

#### featured_branch
**Returns:** A random BranchDrop from a sample of branches that have been set to featured

#### featured_properties
**Returns:** A collection of PropertyDrop's that have been set to be featured

#### googleplus_uri
**Returns:** A string URL for the Agency's googleplus page

#### has_social_links
**Returns:** A boolean whether any of the social links have been set

#### lettings_enabled
**Returns:** Boolean for if lettings are enabled

#### linkedin_uri
**Returns:** A string URL for the Agency's linkedin page

#### logo
**Returns:** A MrRichardImage for the Agency logo

#### locations
**Returns:** A collection of specific locations defined by the Agency

#### menu(menu_id)
**Returns:** A MenuDrop<br/>
**Expects:** A menu_id as a string from a choice of ['primary', 'secondary']

#### menus
**Returns:** All the MenuDrop's for the Agency

#### page(page_id)
**Returns:** A specific CRMPageDrop cms page object<br/>
**Expects:** A string page_id

#### page_categories
**Returns:** An array of all categories used for pages for the Agency site

#### pages
**Returns:** A collection of CRMPageDrop's for the Agency
**Limit:** Page size is 10

#### properties_from_tag(tag)
**Returns:** A collection of properties by a specific tag<br/>
**Expects:** A string tag, such as 'house' or 'garden' etc<br/>
**Limit:** 10

#### properties_with_videos
**Returns:** A collection of properties that have video's<br/>
**Limit:** 10

#### portal_logo
**Returns:** A MrRichardImage for the Agency specific Portal logo

#### recent_lettings_properties
**Returns:** A collection of the latest lettings properties<br/>
**Limit:** 10

#### recent_properties
**Returns:** A collection of the latest properties<br/>
**Limit:** 10

#### recent_sales_and_lettings_properties
**Returns:** A collection of the latest sales and lettings properties<br/>
**Limit:** 10

#### recent_sales_properties
**Returns:** A collection of the latest sales properties<br/>
**Limit:** 10

#### sales_enabled
**Returns:** A boolean to represent if the Agency has sales properties

#### staff_profiles
**Returns:** A collection of all the StaffMemberDrop's for the agency

#### subdomain
**Returns:** The subdomain for the Agency site as a string

#### twitter_uri
**Returns:** A string for the URL of the twitter page

#### website_live
**Returns:** A boolean representation if the website has been published live

#### website_logo
**Returns:** A MrRichardImage of the Agency's website specific logo. This can be used if the original logo does not work well on the site
