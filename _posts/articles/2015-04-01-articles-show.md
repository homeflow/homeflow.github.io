---
layout: default
title: Articles show
modal-id: articles-show
category: articles
---
The article show page is simply a ``show.liquid`` file in your articles directory that has access to the article object:

{% highlight html %}
{% raw %}

<div class="article-show">
 <h2 >{{ article.title }}</h2>
 {% if article.image %}
  <img src="{{ article.image | url_for_generic_image: "270x187" }}">
 {% endif %}
 <div class="article-content">
  {{ article.content }}
 </div>
</div>

{% endraw %}
{% endhighlight %}



