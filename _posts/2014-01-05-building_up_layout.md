---
layout: default
title: Building up the layout
modal-id: building-up-the-layout
---
Other than the Liquid directives in the head section, the ``content_for_layout`` we saw earlier and the Ctesius boot, the ``application.liquid`` file is constructed just the same as a regular web page - add your classes and IDs, divs and CSS in the normal way and style them up using your theme CSS. Be sure to to put it in the stylesheets directive and make sure the names match up:

{% highlight html %}
{% raw %}
{{ "your_theme_css" | theme_stylesheet_link_tag }}
{% endraw %}
{% endhighlight %}

We talk more about images later but for now, add your agency's/portal's logo into the ``/assets/images`` folder and reference it in your application markup as follows:

{% highlight html %}
{% raw %}
<img src="{{'your_image.png' | theme_image_url : "70x70" }}" />
{% endraw %}
{% endhighlight %}

You will notice that we have added a Liquid directive straight into the source of the image. Liquid will expect there to be an image of the name and extension quoted in your theme images folder (``/assets/images``). Also note that we've added an arguement on the end to ask Liquid to resize the image on the server, then send it to the browser - neat.