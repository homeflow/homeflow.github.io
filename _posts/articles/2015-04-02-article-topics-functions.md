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

This next assign statement gets all articles of a certain topic, or in the example shown it actually returns articles for either 'Press Release' or 'News' topics using comma separated values.

Note: These are case sensitive and also require no spaces between the words.

{% highlight liquid %}
{% raw %}
  {% assign other_articles = 'Press Release,News' | articles_by_topic %}
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
