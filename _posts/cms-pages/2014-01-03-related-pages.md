---
layout: default
title: Related pages
modal-id: related-pages
category: cms-pages
---
Pages that share a category can be extracted and looped through using the related pages function:

{% highlight liquid %}
{% raw %}
{% if cms_page.category %}
 {% assign length = cms_page.related_pages | size  %}
  {% if length > 1 %}
   <span class="title">{{cms_page.category}}</span>
   {% for page in cms_page.related_pages %}
    <a class="{% if page.title == cms_page.title %}active{% endif %}" href="/pages/{{ page.uri }}">
     {{page.title}}
    </a>
   {% endfor %}
  {% endif %}
{% endif %}
{% endraw %}
{% endhighlight %}