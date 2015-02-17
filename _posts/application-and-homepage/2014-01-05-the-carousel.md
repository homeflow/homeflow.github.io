---
layout: default
title: The carousel
modal-id: carousel
category: application-and-homepage
---
Your first port of call is to head to the carousel section within the agency or portal admin. You can find that under ``Website/carousel``. Don't worry about the settings for now but instead go straight to ``Add item``. Keep the standard option selected and upload your background image, add a title, a standfirst (the chunk of accompanying text) and a link if required. The minimum you'll want is an image and standfirst.

Now return to you theme and the ``home/home.liquid`` file. This is one place, and a logical one, where we can add our carousel code:

{% highlight html %}
{% raw %}
<ul>
 {% for item in agency.carousel_items %}
  <li style="background-image:url({{item.image | url_for_generic_image}})">
   <div class="slide-content">
    <h2>
     {% if item.link_url != empty %}
      <a href="{{ item.link_url }}" class="link_url" title="{{item.title}}">
     {% endif %}
     {{item.title}}
     {% if item.link_url != empty %}
      </a>
     {% endif %}
    </h2>
    <p>
     {{item.standfirst | truncate: 200}}
    </p>
   </div>
  </li>
 {% endfor %}
</ul>
{% endraw %}
{% endhighlight %}

Whilst we're covering the carousel and ``home.liquid`` it's worth pointing out that your carousel doesn't have to reside in ``home.liquid``. Sometimes it doesn't make sense for everything that is featured on the home page to be in home.liquid. On occasions where we want to include content on the home page but you'd rather add it to ``application.liquid``, you can use the following statement:

{% highlight html %}
{% raw %}
{% if page.controller_name == 'home' %}
 *content*
{% endif %}
{% endraw %}
{% endhighlight %}

And for a handy reference as to what controller is being used, you can add the controller and action as a class to the body tag then inspect the source:

{% highlight html %}
{% raw %}
<body class="{{page.controller_name}} {{page.action_name}}">
{% endraw %}
{% endhighlight %}