---
layout: default
title: Custom theme colours
modal-id: custom-theme-colours
category: application-and-homepage
---
By navigating to your admin area, then following this link: ``/configure/website/appearance/colours``, you can specify custom theme colours that you can then query in your CSS. These configuration options are particularly useful if you're developing a theme that will be used by multiple agencies but also if you want to manage your theme's colours in one place. Simply add your colour using hex notation and query it on your CSS:

``color: {% raw %}{{theme_preferences.primary_colour}};{% endraw %}``

- ``{% raw %}{{theme_preferences.primary_colour}};{% endraw %}``
- ``{% raw %}{{theme_preferences.primary_text_colour}};{% endraw %}``
- ``{% raw %}{{theme_preferences.accent_colour}};{% endraw %}``
- ``{% raw %}{{theme_preferences.accent_text_colour}};{% endraw %}``
- ``{% raw %}{{theme_preferences.accent_tint_colour}};{% endraw %}``
- ``{% raw %}{{theme_preferences.header_background_colour}};{% endraw %}``
- ``{% raw %}{{theme_preferences.navigation_primary_background_colour}};{% endraw %}``
- ``{% raw %}{{theme_preferences.on_navigation_primary_text_colour}};{% endraw %}``
- ``{% raw %}{{theme_preferences.footer_colour}}{% endraw %}``
- ``{% raw %}{{theme_preferences.on_footer_text_colour}};{% endraw %}``
- ``{% raw %}{{theme_preferences.site_background_colour }};{% endraw %}``
- ``{% raw %}{{theme_preferences.button_primary_colour}};{% endraw %}``
- ``{% raw %}{{theme_preferences.button_text_colour }};{% endraw %}``
- ``{% raw %}{{theme_preferences.on_white_heading_text_colour}};{% endraw %}``
- ``{% raw %}{{theme_preferences.custom_colour_x}};{% endraw %}``