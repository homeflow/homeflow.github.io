---
layout: default
title: Child Themes
modal-id: child-themes
category: best-practices
---
When making a theme it is best to only include the base functionality that theme requires. The most logic (especially agent specific) we put into the base themes the more polluted the code gets and harder to extend/read.

You can extend from another theme by simply adding the following to the config.yml file (mentioned below in more detail):

{% highlight html %}
parent_theme: ‘theme_name’
{% endhighlight %}

Any view, partial or file you create in the child theme will override the parent version. This means you can enhance and extend an existing theme by overriding these files.

**when to use child themes**

You should consider moving code into a child theme when the changes you are making are specific to a single user of your theme or it may become more difficult for your theme to be reconfigured in the future, we like to keep themes as flexible and re-useable as possible and child themes are an effective way of achieving this while still catering to agency specific requirements. 
