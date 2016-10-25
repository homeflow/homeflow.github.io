---
layout: default
title: Infinite scroll
modal-id: infinite-scroll
category: articles
---
In order to enable infinite scroll for articles you need to specify the initial containing element that is to be appended with the infinite scroll template.

{% highlight html %}
{% raw %}
  <div id="infinite_pages">
    {% for article in agency.articles %}
      {% include 'articles/article_partial' %}
    {% endfor %}
  </div>
{% endraw %}
{% endhighlight %}

Below is an example of defining the infinite scroll template which is used to render the subsequent blocks of article results at the end of the infinite_pages element.

{% highlight html %}
{% raw %}
 <script id="infinite_scroll_articles_template" type="text/liquid">
    {% for item in articles %}
        <div class="masonry-item">
          <h3><a href="/articles/{{item.slug}}">{{item.title}}</a></h3>
          {% if item.promo_image %}
            <div class="promo-image-wrapper">
              <a href="/articles/{{item.slug}}" class="promo_image">
                <img src="{{item.promo_image | url_for_generic_image : "378x_" }}"/>
              </a>
            </div>
          {% endif %}
          <span class="promo">{{ item.promo | truncatewords: 65 }} <a href="/articles/{{item.slug}}">Continue Reading</a></span>
        </div>
    {% endfor %}
</script>
{% endraw %}
{% endhighlight %}

You also need to enable infinite scroll like so:

{% highlight html %}
{% raw %}
  Ctesius.addConfig('enable_article_infinite_scroll', true);
{% endraw %}
{% endhighlight %}

Auto scrolling can be turned on or off with the following:

{% highlight html %}
{% raw %}
  Ctesius.addConfig('autoscroll_infinite_scroll', false);
{% endraw %}
{% endhighlight %}

### Article JSON
