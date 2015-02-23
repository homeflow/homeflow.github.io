---
layout: default
title: Getting started
modal-id: getting-started
category: user-profile-system
---
The user profile system consists of a number of pre-built templates that can be included in your theme. The first step is to include the default `js_templates` partials which contain the standard HTML for the blocks to be rendered:

{% highlight html %}
{% raw %}
 {% include 'layouts/js_templates' %}
{% endraw %}
{% endhighlight %}

The list of views are below. You can override each of the views that the JS renders by creating files of the same name in a ``layouts/js_templates`` folder in your theme:

- js_templates/_profile.liquid
- js_templates/_profile_account.liquid
- js_templates/_profile_user_info.liquid
- js_templates/_profile_forgotten_password.liquid
- js_templates/_profile_saved_searches.liquid
- js_templates/_profile_saved_properties.liquid
- js_templates/_saved_properties.liquid
- js_templates/_branch_map_pin.liquid
- js_templates/_map_bubble_popup.liquid

If all as gone well you should be able to launch the user profile lightview by adding ``/#user`` on to your staging URL. The jQuery plugin Colorbox is used for the lightview based templates. If you would like access to the source of the templates as a basis for custom development, please see the Stabilisers theme. 