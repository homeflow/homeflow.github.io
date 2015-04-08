---
layout: default
title: Articles loop
modal-id: articles-loop
category: articles
---
Articles are loaded via the agency admin link: ``/configure/website/content/articles``. They can then be queried anywhere on a theme using the agency articles loop. Here's an example construct:

{% highlight html %}
{% raw %}

{% for article in agency.articles limit: 3 %}
 <div class="list-news">
  {% if article.promo_image %}
   <a href="/articles/{{ article.slug }}" title="{{article.title}}">
    <img src="{{ article.promo_image | url_for_agency_logo : "60x60" }}" />
   </a>
  {% endif %}
  <h5>
   <a href="/articles/{{ article.slug }}">
    {{article.title}}
   </a>
  </h5>
  <p>{{article.promo}}</p>
 </div>
{% endfor %}

{% endraw %}
{% endhighlight %}
