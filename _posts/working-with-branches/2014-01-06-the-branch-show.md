---
layout: default
title: The branch show page
modal-id: the-branch-show
category: working-with-branches
---
Wherever we have a Liquid tag that looks like ``{% raw %}{{ branch | url_for_branch}}{% endraw %}`` or if the branch URL is called, the branch show page will get called into action. As with all of the subjects, the branch show page is simply titled ``show.liquid`` and lives in the branches folder.

The branch show page supports many of the things we saw on the property show page - for instance, you could have a JavaScript based carousel showing branch photos, list the staff members belonging to a branch, output the branch description and so on. What information you fetch and how you display it will of course depend on your design, but let's run through the basics:

To get the branch name we use the branch drop and name: ``{% raw %}{{branch.name}}{% endraw %}``. Moving on, we can then fetch the branch description:

{% highlight html %}
{% raw %}
{% if branch.description_with_agency_fallback %}
<p>
 {{branch.description_with_agency_fallback | strip_html}}
</p>
{% endif %}
{% endraw %}
{% endhighlight %}

This nifty bit of code will try and get the branch description, but if it's empty, we'll get the agency description. Note that it is unlikely an agent will not have a description for their branch AND their agency, but it's always good practice to check. Notice also we're stripping the HTML as sometimes some links and other formatting gets added to the description which can wreak havoc on our layout.

Staff profiles are a whole subject unto themselves which we will look at later in the documentation but for now, if you wanted to display some mini profiles with links to full profiles, or just give you branch pages the human touch, you could use something like:

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

Everything here should be reasonably familiar to you, though note we've added a ``limit`` to our for loop so that a maximum of six profiles are extracted. Also note that we're referencing a fallback image directly. Whilst this is a quirk of this code copied from a theme, sometimes you might need to reference an image using its relative path. On the whole though, you can just use Liquid and ``theme_image_url``.