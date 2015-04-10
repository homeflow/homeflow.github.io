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
   <a href="https://twitter.com/{{ agency.twitter_screen_name }}" target="_blank">
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