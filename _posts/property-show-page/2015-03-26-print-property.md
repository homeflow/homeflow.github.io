---
layout: default
title: Print property
modal-id: print-property
category: property-show-page
---
Printing using our core print page and stylesheet is simple to get going. Simply add a print anchor to your property show page and point its href to ``{% raw %}{{property | url_for_property}}{% endraw %}/print``. If you need to modify the template, add a ``show_print.liquid`` (no preceeding underscore needed) in your properties directory, then ask a member of Homeflow to drop the template in. You can also create one from scratch if you'd ``rather``.