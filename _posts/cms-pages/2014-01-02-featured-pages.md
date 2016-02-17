---
layout: default
title: Featured pages
modal-id: featured-pages
category: cms-pages
---

Featured pages are available through the agency drop throughout the site by calling `` agency.featured_pages `` this will return a collection of cms_page drops containing only pages which have `` feature on homepage `` set to true.

{% highlight html %}
{% raw %}
  {% for page in agency.featured_pages %}
      ...
  {% endfor %}
{% endraw %}
{% endhighlight %}
