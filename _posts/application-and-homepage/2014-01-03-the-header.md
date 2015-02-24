---
layout: default
title: The header
modal-id: header
category: application-and-homepage
---
A header would probably consist of the agency or portal logo.

In the agency admin, go to ``Website/Appearance/Logos`` and upload your logo<br>
In the portal admin, go to ``Configure/Appearance/Logos`` and upload your portal logo.

Now in your source, within your header tags or header div tags, add:

Agency:<br>
{% highlight html %}
{% raw %}
<img src="{{ agency.logo | url_for_agency_logo }}" alt="{{agency.name}} logo" />
{% endraw %}
{% endhighlight %}

Portal:<br>
{% highlight html %}
{% raw %}
<img src="{{ portal.website_logo | url_for_portal_logo }}" alt="{{portal.name}}" />
{% endraw %}
{% endhighlight %}