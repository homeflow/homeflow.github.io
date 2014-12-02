---
layout: default
title: Other staff drops
modal-id: other-staff-drops
category: appendix
---
``{% raw %}{{staff_member.first_name}}{% endraw %}``

``{% raw %}{{staff_member.agency}}{% endraw %}``

``{% raw %}{{staff_member.branch}}{% endraw %}``

``{% raw %}{{staff_member.direct_line}}{% endraw %}``

If entered on the system, the staff member's direct dial number.

``{% raw %}{{staff_member.name_without_acronyms}}{% endraw %}``

Some staff names contain lengthy qualification acronyms that can cause layout problems - use this to strip these acronyms.

``{% raw %}{{staff_member.video_uri}}{% endraw %}``

If the staff member has a video URL entered on the system, this field will retrieve it. Note there's no guarantee what format or type of link this will be.


