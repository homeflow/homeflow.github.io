---
layout: default
title: Problem Solving
modal-id: problem-solving
category: best-practices
---

You will inevitably encounter problems, so here are a few steps to try to resolve issues before asking for help.

<br>

#### Check the Documentation

Read the relevant pages in this documentation and even some of the more general pages, as the solution may be explained somewhere unexpected. Check the documentation on [drops](/drops) if you have a question about which variables are available from a template.

You should also refer to the [Liquid documentation](https://help.shopify.com/themes/liquid) or [Liquid for designers](https://github.com/Shopify/liquid/wiki/liquid-for-designers) wiki if your issue is liquid-specific. the former contains a comprehensive list of the built-in tags, objects and filters (although, depending on the version of Liquid used by Ctesius at the time, some newer features of the language may not be available).

<br>

#### Search for The Solution Online

If you encounter a problem that isn't specific to Homeflow's systems and tools - but a more general programming issue, you should try to find a solution using [Google](https://www.google.co.uk/) or [Stack Overflow](http://stackoverflow.com/). Most issues related to HTML, CSS, JavaScript and Liquid can be solved this way.

<br>

#### Debugging Liquid

Inspecting the values of variables at different points in your code is a good way to identify where problems are occuring. You can use JavaScript to output resolved Liquid statements to the browser's console:

{% highlight javascript %}
{% raw %}
console.log('Bedrooms: {{ property.bedrooms }}');
{% endraw %}
{% endhighlight %}

<br>

#### Debugging JavaScript

JS issues are often due to the order the code is executed. Any code that requires elements of the DOM to be loaded *before* it runs should be placed inside one of the jQuery functions ``$(document).ready()`` or ``$(function())``.

``Ctesius.init()`` should be called **after** all config settings and event registers.

<br>

#### Ask Homeflow For Help

If you are unable to solve the issue yourself, ask the Homeflow dev team for help.

When asking a question, make sure it contains all the information we might need. Include the location of the file you're working on within the project, a link to the page on the staging site, any error messages you have encountered as well as the things you've already tried to resolve the issue. This will give us the best chance of giving you a prompt and helpful response.

You can email us at [developer-support@homeflow.co.uk](mailto:developer-support@homeflow.co.uk)
