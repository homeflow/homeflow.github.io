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

If you are planning on using infinite scroll on pages where you have articles for a specific topic you will need to call the following variation on button click to pass in the selected topic:

{% highlight html %}
{% raw %}
  Ctesius.Models.ArticleInfiniteScroll.loadNextByTopic('{{articles.first.topic}}')
{% endraw %}
{% endhighlight %}


### Article JSON
The articles infinite scroll uses a liquid JSON (LJSON) partial named ``_articles_list.ljson`` an example of this file can be found in the stabilisers theme [here](https://github.com/homeflow/stabilisers/blob/master/articles/_articles_list.ljson).

If you want to override this file for any variations or if you need any missing article methods then you can make your own file in the articles folder in your theme.
