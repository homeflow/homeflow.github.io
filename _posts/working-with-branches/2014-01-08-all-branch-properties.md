---
layout: default
title: All branch properties
modal-id: all-branch-properties
categories: working-with-branches
---
If you would like to display all properties that belong to a branch with pagination, we'll need a ``properties.liquid`` file within the branches folder. Once you have this you can start to build up the layout. This will most likely be a hybrid of your properties result page and your branch show page so use partials where possible and reuse what you've already written.

To start with, you might want to add a title:

{% highlight html %}
{% raw %}
<h1>{{agency.name}} - {{branch.name}} branch - All {{current_channel}}</h1>
{% endraw %}
{% endhighlight %}

Not much new here but it's worth knowing that ``{% raw %}{{current_channel}}{% endraw %}`` will return either a 'Sales' or 'Lettings' string. Next you might want some tabs that will enable the user to navigate around:

{% highlight html %}
{% raw %}
<ul class="nav-menu nav-tabs">
 <li><a href="{{branch | url_for_branch : branch.agency}}#tabs/summary" id="tab_summary">Summary</a></li>
 <li><a href="#tabs/team" id="tab_team">Meet our team</a></li>
 {% if branch.sales_branch_properties_count > 0 %}
  <li><a href="{{branch | url_for_branch : branch.agency}}/sales" id="sales">Our sales</a></li>
 {% endif %}
 {% if branch.lettings_branch_properties_count > 0 %}
  <li><a href="{{branch | url_for_branch : branch.agency}}/lettings" id="lets">Our lettings</a></li>
 {% endif %}
</ul>
{% endraw %}
{% endhighlight %}

The first two tabs here would be hidden tabs on the page that get selected and displayed on a click. The branch properties tabs however, need to go through the branch properties controller to get the results. All we need do here is specify the appropriate branch URL with ``/sales`` or ``/lettings``. If you're developing a portal with agencies that have multiple branches, you will need to use ``{% raw %}{{branch | url_for_branch : branch.agency}}{% endraw %}`` in your URL, else you can just use ``{% raw %}{{branch | url_for_branch}}{% endraw %}``.

Next we need to output the actual results that are returned from our request. Thankfully this is just the same as outputting our property results seen earlier so you will have your pagination header, property loop, property small output and footer pagination (if required).