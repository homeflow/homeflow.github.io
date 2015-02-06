---
layout: default
title: Page titles and descriptions
modal-id: page-titles-and-descriptions
category: application-and-homepage
url: /application-and-homepage/#page-titles-and-descriptions
---
The Homeflow API allows you to fully customise your page titles and descriptions; not only for the home page but for other categories of page as well.

To configure your home page and main titles, you will need to take a first foray into the Agency/Portal admin. To do this you use a link similar to the two links outlined before:

Agencies: ``http://agency_homeflow_domain.homeflow.co.uk/admin``<br>
Portals: ``http://portal_homeflow_domain.portal.homeflow.co.uk/admin``

We'll assume you have been provided with your login.

Now head to ``/configure/website/appearance/titling``. It should be fairly self-explanatory from here.

To publish the titles and keywords to your theme, all you need do is add the following Liquid tags between the normal HTML tags in your ``application.liquid`` source:

{% highlight html %}
{% raw %}
<title>{{page.page_title}}</title>
<meta name="title" content="{{page.page_title}}" />
<meta name="description" content="{{page.page_description}}" />
{% endraw %}
{% endhighlight %}

Homeflow has a general fallback for each category of page should you not opt to customise the wording. Should you want to customise your titles and descriptions, head to: ``/configure/website/content/content/list``. If you scroll down you will see the various chunks available for the different categories of page. We tend to add a mixture of Liquid and plain text to give the user or indeed the search engine some useful information. For example, a typical ``property details`` page title could be:

{% highlight html %}
{% raw %}
{% unless property.bedrooms == 0 %}
  {{property.bedrooms}} bedroom
{% endunless %}
property {{current_channel.dictionary.preposition}} in {{property.display_address}}
{% endraw %}
{% endhighlight %}

This might output something like: ``3 bedroom property for sale in Temple Street, Brighton``.

This is the first ``unless`` tag we've seen - like PHP and many other languages, the output is always true ``unless`` a condition is met. In this instance we're checking whether bedrooms is not zero before outputting. A couple of other tags are:

{% highlight html %}
{% raw %}
{{current_channel.dictionary.preposition}}
{% endraw %}
{% endhighlight %}

This tag outputs either 'for sale' or 'to let'.

{% highlight html %}
{% raw %}
{{property.display_address}}
{% endraw %}
{% endhighlight %}

This tag outputs the display address - normally a filtered version of the actual address.