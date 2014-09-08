---
layout: default
title: The carousel
modal-id: the-carousel
---
Many agency sites and indeed portals have what we refer to as a ``carousel`` on their home page. This is a gallery of images with text overlays designed to give the user an attractive initial presentation and to give your site the 'wow' factor. At the time of writing, many theme developers are using full width images within their carousel as well as responsive images to cater for different viewports.

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

There are numerous ways you can use the carousel - some themes have a small photo box whereas others go full width with the photos. In the example above, we are going full width with our carousel image set as a background against the ``li`` for each carousel item using a for loop. As you can see, we check if the ``link_url`` is empty and if not, we wrap out title with the link URL. We then output our standfirst and in this case we truncate it to two hundred characters (more on truncate in a bit). Note that we could run a check on standfirst but here we're assuming a standfirst has been entered for each carousel item.

Whilst we're covering the carousel and ``home.liquid`` it's worth pointing out that your carousel doesn't have to reside in ``home.liquid``. Many front pages are split into different sections and sometimes it doesn't make sense for everything that is featured on the home page to be in home (by the way the ``home.liquid`` file is automatically included into the ``{% raw %}{{content_for_layout}}{% endraw %}`` yield when on the site's root). On occasions where we want to include content on the home page but you'd rather add it to ``application.liquid``, you can use the following statement:

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