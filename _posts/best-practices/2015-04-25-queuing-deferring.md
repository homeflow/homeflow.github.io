---
layout: default
title: Queuing and deferring JavaScripts
modal-id: queuing-deferring-js
category: best-practices
---
The real world speed of a site and Google PageSpeed scores will suffer if JavaScript is block rendered in the head section. That being said, moving all JavaScript, especially library files, to the foot of a page can cause errors. What we need is a reliable way to capture document ready calls, queue them, then execute them once our deferred JavaScripts are loaded. Using our async functions, we can do just that.

To get up and running, firstly you need to set up your asset packs and vendor assets as seen in the previous chapter. Once done, you can render the blobs to the page with our async head and foot includes:

{% highlight html %}
{% raw %}
<head>
 <link href="/vendor_assets/blob.css" rel="stylesheet" type="text/css" />
 {% include 'js_templates/async_head' %}
</head>
{% endraw %}
{% endhighlight %}

{% highlight javascript %}
{% raw %}
  {% include 'js_templates/async_foot_function' %} 
  <script src='/vendor_assets/blob.js' type='text/javascript' async onload="async_foot();" ></script>
 </body>
</html>
{% endraw %}
{% endhighlight %}

Note: the includes are grabbed from our core app, so you don't need to create the files locally in your theme.

That should in principle be all you need.