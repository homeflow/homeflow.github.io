---
layout: default
title: Best Practices
modal-id: best-practices
category: application-and-homepage
---
The Homeflow system uses various levels of caching amongst other techniques to deliver content super fast to the user's browser. That being said, there is no substitute for coding your theme in the most efficient way possible. This section will explore how to do that and will introduce some functions we have created to help you in your quest for speed. Google has an excellent tool called [PageSpeed Insights](https://developers.google.com/speed/pagespeed/insights/) that you can use to review your site.

### Working with Images

Images must be the number one culprit in terms of slow downloads from the server. Any image that runs through our Liquid filters will get compressed. Here's some ways you can achieve this:

{% highlight html %}
{% raw %}
<img src="{{ portal.website_logo | url_for_portal_logo : "200x200" }}" />

<img src="{{ portal.website_logo | url_for_portal_logo : "_x_" }}" />

<img src="{{ portal.website_logo | url_for_portal_logo : "200x_" }}" />

<img src="{{ portal.website_logo | url_for_portal_logo : "_x200" }}" />
{% endraw %}
{% endhighlight %}

Basically any size dimensions or our nifty ``x`` function will see the image pass through the filters.

### Minifying JavaScript and CSS

Our second good practice is to minify your JS and CSS where possible. Most jQuery plugins and CSS can be acquired in a minified state, so if that's an option, take it. If your own JS and CSS will rarely be modified after going live, we can minify it for you automatically. Here's how:

- In your theme's ``config.yml`` file, you will need a construct such as this:

{% highlight yaml %}
  asset_packs:
    javascript:
      - respond
      - vendor/jquery.mobile.custom.min
      - vendor/bxslider/jquery.bxslider.min
      - vendor/jquery.scrollTo.min
      - vendor/jquery.tooltipster.min
    stylesheet:
      - normalize.min.css
      - dropkick.css
      - main.lcss
      - tooltipster.css
{% endhighlight %}

- If your CSS does not run through Liquid, you will need to denote its CSS extension. If your file lives in a subfolder, you will need to denote this too as shown above.

- Be careful with spacing as YAML files are space sensitive. If you get an error after inserting your directives, remove any tabs and use spaces instead

- To output your minified JS and CSS in your theme, add the following two lines:

{% highlight html %}
{% raw %}
<script src="/liquid_assets/javascript_pack.js"></script>

<link href="/liquid_assets/stylesheet_pack.css" rel="stylesheet" type="text/css" />
{% endraw %}
{% endhighlight %}

### Deferring JS and CSS Declarations

Whilst developing your theme, have a think: does certain JS and CSS file declarations have to be in the head of your source? Can they be deferred before the closing body tag? The Google PageSpeed analysis will demote points from you for block levelling JS and CSS.

In addition, is there code that is only used on certain pages, e.g. property pages? Could you defer the scripts on the results or show page for example? Whilst not forgetting to minify them if that's an option.

These sort of decisions are best made either before or during development, rather than coming back to theme at a later date. With the best will in the world, we all sometimes forget what this or that function or declation is doing!

