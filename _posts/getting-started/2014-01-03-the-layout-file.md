---
layout: default
title: The layout file
modal-id: layout-file
category: getting-started
---
Every page render starts at the layout, which is always found in ``/layouts/application.liquid``. This file will contain the html, head, and body tags and will define the overall 'makeup' of your site.

Take a look at the source in the Stabilisers theme and you will see there's a few things to note. Firstly we link to the default styles and JavaScripts using our first bit of Liquid syntax:

{% highlight html %}
{% raw %}
{{ "application" | javascript_include_tag }}
{{ "application" | stylesheet_link_tag }}
{% endraw %}
{% endhighlight %}

This will bring in all the default styles and some JavaScript libraries which form the basis of every Ctesius theme. As of the latest revision to this documentation, they are:

- Bootstrap
- jQuery - v1.9
- jQuery Cycle - 3.0.3 (11-JUL-2013)
- jQuery Nivo Slider
- Backbone.js -  1.0.0
- Underscore.js - 1.4.3
- leaflet.js
- Font Awesome
- the Homeflow search and profile system

You'll also notice that we make another call:

{% highlight html %}
{% raw %}
{{ "stabilisers" | theme_stylesheet_link_tag }}
{% endraw %}
{% endhighlight %}

There is a subtle different between the two Liquid directives in that the latter has a ``theme_`` directive and the other does not. When you add a theme stylesheet or theme JavaScript directive, the theme will expect the quoted LCSS file to reside in ``/assets/stylesheets`` (``/assets/javascripts`` for JavaScript files). LCSS files are pretty much CSS files run through a Liquid filter. This enables us to customise the CSS easily for different sites. The directive without the theme pointer will load something from the core app.

Continuing with the layout file the next command you'll see is:

{% highlight html %}
{% raw %}
{% include 'layouts/js_templates' %}
{% endraw %}
{% endhighlight %}

This is the first include that we've seen. A bit like PHP includes, Liquid includes allow you include a partial template. This is excellent for including blocks that occur on several pages, or, as we'll see later, in Liquid for loops. Important point: partial names must be preceeded by an underscore `_`. When you call the partial however, no underscore is required though you must put the path in quotes.

The directive here pulls in the default JavaScript templates for the dynamically drawn user sections of the site. They are all overridable so you can design them as you need to. We'll expand more on these templates later.

Perhaps the most important section for the layout is the helper ``content_for_layout``. This outputs the rendered results of the rest of the template.

{% highlight html %}
{% raw %}
{{ content_for_layout }}
{% endraw %}
{% endhighlight %}

In other words, all other template parts are like partials that get evaluated and loaded into this section.

Finally we need to boot the Ctesius system to handle searches, user profiles and so on. To do that we add the following function:  

{% highlight javascript %}
{% raw %}
<script type="text/javascript">
 $(document).ready(function(){
  Ctesius.init()
 });
</script>
{% endraw %}
{% endhighlight %}

This needs to be used after any Ctesius events or config options are set. Some theme developers choose to add this function at the foot of application.liquid whereas others will add it to a theme JavaScripts file, include the directive at the bottom of it, then include the partial.