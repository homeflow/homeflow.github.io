---
layout: default
title: Displaying branch properties
modal-id: displaying-branch-properties
category: working-with-branches
---
The branch properties page is one where we can thankfully reuse our property loops and pagination figures as seen on the property results. Alternatively we can make use of the tabbing facility and include a function that will return some recent sales or recent lettings. If you would like to get the full results and make use of pagination, we'll need to use the former of the two options as the properties method in the branches controller needs to run to return the results and pagination.

Typically branch pages will make use of our built-in tabbing facility as seen earlier for property results. To get the tabs up and running, you will need the following code:

{% highlight html %}
<ul class="nav-menu nav-tabs">
 <li><a href="#tabs/summary" id="tab_summary" class="selected">Summary</a></li>
 <li><a href="#tabs/team" id="tab_team">Meet our team</a></li>
 <li><a href="#tabs/sales" id="tab_sales">Our sales</a></li>
 <li><a href="#tabs/lettings" id="tab_lettings">Our lettings</a></li>
</ul>
{% endhighlight %}

NB: the Ctesius app will take care of adding ``selected active`` classes to your tabs but you will need to style them.