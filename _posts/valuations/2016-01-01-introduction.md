---
layout: default
title: Introduction
modal-id: valuations
category: valuations
---

The Homeflow instant valuation tool (Homeval) can be added to a theme by following these steps:

Add this include statement near the top of the `body` in `application.liquid`

{% highlight html %}
  {% raw %}
    {% include 'valuations/valuation' %}
  {% endraw %}
{% endhighlight %}

Add Ctesius stylesheet to `config.yml` (if it isn't in there already)

```
vendor_assets:
    stylesheets:
      - ctesius
```

Then add a link to `/#/valuation` or `/#valuation` (doesn't matter which) somewhere.

Styling should be straighforward, just make sure any CSS selectors are specific enough to override the existing ones.

The tool will need to be activated for the agent by Homeflow before it will work. Please contact support to request this feature is enabled.

After activation, the link should open the tool in a modal window. Please contact [developer support](mailto:developer-support@homeflow.co.uk) with any issues.

