---
layout: default
title: Branch Drop
modal-id: branch-drop
category: drops
---

Below are the methods available on the BranchDrop, what they return and also what they expect to be passed when calling the method.

#### address_with_line_breaks
**Returns:** The Branch address with line breaks

#### all_recent_lettings_properties
**Returns:** A collection of the latest lettings properties, including those with all statuses (including 'sold' etc).<br/>
**Limit:** 5

#### all_recent_sales_properties
**Returns:** A collection of the latest sales properties, including those with all statuses (including 'sold' etc).<br/>
**Limit:** 5

#### agency
**Returns:** The [AgencyDrop](#agency-drop) for that Branch

#### branch_manager
**Returns:** The branch manager as a StaffMemberDrop

#### contactable_sales_telephone
**Returns:** A string valud for the Branch sales telephone number

#### contactable_lettings_telephone
**Returns:** A string valud for the Branch lettings telephone number

#### contactable_telephone(channel)
**Returns:** A string valud for the Branch telephone number based on the channel<br/>
**Expects:** A string channel of 'sales' or 'lettings'

#### contains_staff_member?(staff_member)
**Returns:** A boolean to check if a staff member is assigned to the Branch<br/>
**Expects** A StaffMemberDrop

#### content_chunks
**Returns:** An array of content chunks, as hashes, where the branch has been set to this one.

#### content_blocks
**Returns:** An array of content chunks, as ContentBlockDrops, where the branch has been set to this one.

#### default_vox_number
**Returns:** The default VOX telephone number as a string

#### description
**Returns:** The Branch description as text

#### description_with_agency_fallback
**Returns:** The Branch description as text and if this is blank then the Branch Agency description is returned

#### facebook_uri
**Returns:** A string URL for the Branch's facebook page

#### googleplus_uri
**Returns:** A string URL for the Branch's googleplus page

#### has_social_links
**Returns:** A boolean if any social links are set

#### hero_asset
**Returns:** The hero image for the Branch as a MrRichardImage

#### lettings_staff_profiles
**Returns:** A collection of StaffProfileDrop's of any lettings negotiators

#### linkedin_uri
**Returns:** A string URL for the Branch's linkedin page

#### member_subscription_level
**Returns:**

#### node(slug)
**Returns:** A specific node associated with the branch.

#### nodes
**Returns:** An array of nodes associated with the branch.

#### photo
**Returns:** The default photo for the Branch as a MrRichardImage

#### photos
**Returns:** A collection of MrRichardImage's for the Branch photos

#### recent_sales_properties
**Returns:** A collection of the latest sales properties<br/>
**Limit:** 5

#### recent_lettings_properties
**Returns:** A collection of the latest lettings properties<br/>
**Limit:** 5

#### recent_properties
**Returns:** A collection of the latest properties<br/>
**Limit:** 5

#### sales_staff_profiles
**Returns:** A collection of [StaffMemberDrops](#staff-member-drop) of any sales negotiators

#### staff_profiles
**Returns:** A collection of [StaffMemberDrops](#staff-member-drop) for all the Branch employees

#### staff_member(staff_member_id)
**Returns:** An individual staff member's [StaffMemberDrop](#staff-member-drop)<br/>
**Expects:** A string staff_member_id

#### ten_recent_lettings_properties
**Returns:** A collection of the latest lettings properties<br/>
**Limit:** 10

#### ten_recent_sales_properties
**Returns:** A collection of the latest sales properties<br/>
**Limit:** 10

#### twitter_uri
**Returns:** A string URL for the Branch's twitter page

#### vox_numbers
**Returns:** A collection of VOX number strings for the branch
