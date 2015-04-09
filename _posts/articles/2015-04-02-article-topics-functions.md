---
layout: default
title: Articles topics and functions
modal-id: articles-topics-functions
category: articles
---
Topics are a useful way of grouping articles. You can loop through and query articles and topics in the same way we've seen in the other articles write-ups:

{% highlight html %}
{% raw %}

{% for article in agency.articles limit: 3 %}
 {% if article.topic == "news" %}
  <div class="promo-panel">
   <p>
    <a href="/articles/topic-{{topic}}">See all our {{topic}} posts</a>
   </p>
  </div>
 {% endif %}
{% endfor %}

{% endraw %}
{% endhighlight %}

Our standard array filters can be used on articles and are useful for building up arrays for asides and other article menus. This function gets all articles but filters out those with a topic of 'news':

{% highlight liquid %}
{% raw %}

{% assign other_articles = agency.articles | delete_by : 'topic', 'news' %}
 
{% endraw %}
{% endhighlight %}

This next assign statement gets all articles of a certain topic (in this case the same topic as the article the user is on) as well as excludes the active article using the 'slug' as the means to do it.

{% highlight liquid %}
{% raw %}

{% assign other_articles = agency.articles | selected_by : 'topic', article.topic | excluding : article , 'slug' %}

{% endraw %}
{% endhighlight %}

You can then loop through the array as you would normally do. Each result is an article object with all its attrbutes:

{% highlight liquid %}
{% raw %}

{% for article in other_articles limit: 5 %}
 <div class="promo-panel grey similar-article">
   <a href="/articles/{{ article.slug }}"><h3>{{ article.title }}</h3></a>
 </div>
{% endfor %}

{% endraw %}
{% endhighlight %}
