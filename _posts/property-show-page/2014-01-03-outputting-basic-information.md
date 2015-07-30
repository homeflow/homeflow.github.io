---
layout: default
title: Outputting basic information
modal-id: outputting-basic-information
category: property-show-page
---
Your first requirement is likely to be an output of the property's address, or at least part of it, and its price in a title:

{% highlight html %}
{% raw %}
<h1>{{property.display_address}}</h1>
<h2>{{property.price}}</h2>
{% endraw %}
{% endhighlight %}

Next you will probably want to output the photos of the property. Many developers use jQuery type photo sliders for displaying and navigating through the photos. Thankfully, by using the photos loop, this is relatively easy to achieve:

{% highlight html %}
{% raw %}
{% for photo in property.photos %}
 <img src="{{ photo | url_for_property_photo : "410x308"}}" height="308" width="410" />
{% endfor %}
{% endraw %}
{% endhighlight %}

And if you just wanted the property's main photo:

{% highlight html %}
{% raw %}
<img src="{{property.main_photo | url_for_property_photo : "410x308"}}" height="308" width="410" />
{% endraw %}
{% endhighlight %}

Next we might want to output the short description for the property:

{% highlight html %}
{% raw %}
{{property.short_description | truncate: 900}}
{% endraw %}
{% endhighlight %}

Then, to get the property's status (Sold, Let, etc), we can use:

{% highlight html %}
{% raw %}
<h4>{{property.status}}</h4>
{% endraw %}
{% endhighlight %}