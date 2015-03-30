---
layout: default
title: Articles loop
modal-id: articles-index
category: articles
---
The articles index is a static file that needs to reside in an ``articles`` folder in your theme. This index can be accessed using the URL ``/articles``:

{% highlight html %}
{% raw %}

<h2>Articles{% if topic %} in {{topic | capitalize}}{% endif %}</h2>

{% for article in articles %}
  <a href="/articles/{{ article.slug }}">
    <div class="article">
      <h3 class="article-header">
        <span class="article-title">{{ article.title }}</span>
      </h3>
      {% if article.promo_image %}
        <img src="{{ article.promo_image | url_for_generic_image : "270x187" }}">
      {% else %}
        <img src="{{ 'article-placeholder.png' | theme_image_url }}">
      {% endif %}
      <div class="article-details">
        <span class="article-date">{{ article.date }}</span>
        {{ article.promo }}... 
        <span class="article-more-link" href="/articles/{{ article.slug }}">more</span>
      </div>
    </div>
  </a>
{% endfor %}

{% endhighlight %}
{% endraw %}