---
layout: default
title: The branch show page
modal-id: the-branch-show
category: branches
---
Wherever we have a Liquid tag that looks like ``{% raw %}{{ branch | url_for_branch}}{% endraw %}`` or if the branch URL is called, the branch show page will get called into action. As with all of the subjects, the branch show page is simply titled ``show.liquid`` and lives in the branches folder.

The branch show page supports many of the things we saw on the property show page. To get the branch name we use the branch drop and name: ``{% raw %}{{branch.name}}{% endraw %}``. Moving on, we can then fetch the branch description:

{% highlight html %}
{% raw %}
{% if branch.description_with_agency_fallback %}
<p>
 {{branch.description_with_agency_fallback | strip_html}}
</p>
{% endif %}
{% endraw %}
{% endhighlight %}

Ff you wanted to display some staff profiles with links to full profiles, you could use something like:

{% highlight html %}
{% raw %}
{% unless branch.staff_profiles.size == 0 &}
 <div class="sm_staff_gallery">
 {% for staff_member in branch.staff_profiles limit:6 %}
  {% if staff_member.avatar %}
   <a href="{{ staff_member | url_for_staff_member}}" title="{{staff_member.name}}">
   <img src="{{ staff_member.avatar | url_for_staff_profile_avatar : "40x40" }}" title="{{staff_member.name}}">
   </a>
  {% else %}
   <a href="{{ staff_member | url_for_staff_member}}" title="{{staff_member.name}}">
   <img src="/liquid_assets/images/sp.jpg" height="40" width="40" title="{{staff_member.name}}">
   </a>
  {% endif %}
 {% endfor %}
 </div>
{% endunless %}
{% endraw %}
{% endhighlight %}

#####Map Zoom levels
If you need to manually set the zoom level of the branch map you can do so with the following snippet (replace 15 with any fallback zoom level you wish):

{% highlight html %}
{% raw %}
    Ctesius.addConfig('custom_map_zoom', {% if agency.preferences.google_maps_branch_zoom_level %}{{agency.preferences.google_maps_branch_zoom_level}}{% else %}15{% endif %});
{% endraw %}
{% endhighlight %}