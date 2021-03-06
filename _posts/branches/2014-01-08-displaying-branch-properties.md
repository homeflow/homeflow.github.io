---
layout: default
title: Displaying branch properties
modal-id: displaying-branch-properties
category: branches
---
The branch properties page is one where we can thankfully reuse our property loops and pagination figures as seen on the property results. If you would like to display all properties that belong to a branch with pagination, we'll need a ``properties.liquid`` file within the branches folder. In it, add the path to your search results:

{% highlight liquid %}
{% raw %}
{% include 'property_search/results' %}
{% endraw %}
{% endhighlight %}

We can then link to the branch properties page using the following;

{% highlight html %}
{% raw %}
<a href="{{branch | url_for_branch }}/sales">See all {{branch.name}} sales</a>

<a href="{{branch | url_for_branch }}/lettings">See all {{branch.name}} lettings</a>
{% endraw %}
{% endhighlight %}