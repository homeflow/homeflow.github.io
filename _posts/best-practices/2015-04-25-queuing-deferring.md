---
layout: default
title: Queuing and deferring JavaScripts
modal-id: queuing-deferring-js
category: best-practices
---
The real world speed of a site and Google PageSpeed scores will suffer if JavaScript is block rendered in the head section. That being said, moving all JavaScript, especially library files, to the foot of a page can cause errors. What we need is a reliable way to capture document ready calls, queue them, then execute them once our deferred JavaScripts are loaded. Using our async functions, we can do just that.

To get up and running, firstly you need to set up your asset packs and vendor assets as seen [here](/assets#assets-and-minify). Once done, you can render the blobs to the page with our async head and foot includes:

{% highlight html %}
{% raw %}
<head>
 <link href="/vendor_assets/blob.css" rel="stylesheet" type="text/css" />
 <script src='/vendor_assets/blob.js' type='text/javascript' async onload="async_foot();" ></script>
 {% include 'js_templates/async_head' %}
</head>
{% endraw %}
{% endhighlight %}

{% highlight javascript %}
{% raw %}
   {% include 'js_templates/async_foot_function' %} 
 </body>
</html>
{% endraw %}
{% endhighlight %}

We would strongly recommend integrating the async work (if you choose to use it) into your theme on inception, as re-engineering a theme to support async work can sometimes produce errors. More of often than not, this is because the deferred JavaScript isn't ready for when some of the functions are called. To get round this, simply put your functions in a document ready. 