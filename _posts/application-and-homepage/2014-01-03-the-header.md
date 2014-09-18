---
layout: default
title: The header
modal-id: header
category: application-and-homepage
---
A header would probably consist of the agency or portal logo, so let's take a first foray into the Agency or Portal admin, add the logo, then pull it out and plug it into the source using Liquid. Note that if you'd rather just add or keep your logo in ``/assets/images`` that's absolutely fine.

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

There's a couple of new things here - the first is we need a ``key`` when referencing an agency or portal logo (and many other things as we'll see) and we're using the agency and portal Liquid name tag to fill in the alt attribute of the image. As you become more experienced with your template(s) you will find there's some useful and sometimes innovative ways you can use tags.