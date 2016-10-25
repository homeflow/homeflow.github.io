---
layout: default
title: Social media functions
modal-id: social-media
category: appendix
---
A function exists that can query the twitter api in order to pull back a number of tweets for an agency. Twitter keys are added in agency admin under website/appearance/preferences section, whilst the agency's screen name can be set by a member of the Homeflow team. Here's the code required:

{% highlight html %}
{% raw %}

{% if
 agency.twitter_consumer_key != "" or
 agency.twitter_secret != "" or
 agency.twitter_token != "" or
 agency.twitter_screen_name != ""
%}

{% twitter_user_timeline screen_name : agency.twitter_screen_name %}
 {% for tweet in tweets limit: 3 %}
  <p class="tweet">
   <a href="https://twitter.com/{{ agency.twitter_screen_name }}">
    <strong>{{ twitter_user.name }}</strong>
    <span>@{{ agency.twitter_screen_name }}</span>
   </a>
   <span class="tweet_date">
    {{ tweet.created_at | date: "%d %B" }}
   </span>
   {{ tweet.text | auto_link }}
  </p>
 {% endfor %}
{% endtwitter_user_timeline %}

{% endraw %}
{% endhighlight %}

### Social media sharing
You can easily add share links to any of your pages for social media with the following snippet:

{% highlight html %}
{% raw %}
<aside class="social-share">
    <h2>Share this:</h2>
    <ul>
        <li class="twitter"><a href="https://twitter.com/intent/tweet?url={{ site.url }}{{ page.url }}{% if page.description %}&text={{ page.description | url_escape }}{% else %}{{ page.title | url_escape }}{% endif %}{% if site.twitter %}&via={{ site.twitter }}{% endif %}" title="Share on Twitter">Twitter</a></li>

        <li class="facebook"><a href="https://www.facebook.com/sharer/sharer.php?u={{ site.url }}{{ page.url }}{% if page.description %}&t={{ page.description | url_escape }}{% else %}{{ page.title | url_escape }}{% endif %}" title="Share on Facebook">Facebook</a></li>

        <li class="googleplus"><a href="https://plus.google.com/share?url={{ site.url }}{{ page.url }}" title="Share on Google Plus">Google+</a></li>
    </ul>
</aside>
{% endraw %}
{% endhighlight %}
