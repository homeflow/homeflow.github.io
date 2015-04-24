---
layout: default
title: Infinite scroll options
modal-id: infinite-scroll-options
category: property-results
---
**Overlays**

The function also ships with a loading overlay should you want to use it. It is a simple fullscreen fade in and out whilst the properties are being fetched. If you'd rather not have it displayed, you can simply place it far off screen so even when it's triggered it cannot be seen:

{% highlight javascript %}
{% raw %}
$('.loading').css('left', '9999px')
{% endraw %}
{% endhighlight %}
<br>
**Load more on click**

If you would prefer to load results on a button press, add the config below:

{% highlight javascript %}
{% raw %}
Ctesius.addConfig('autoscroll_infinite_scroll', false);
{% endraw %}
{% endhighlight %}

Next, add your anchor or button and provide it with an onclick kick event:

{% highlight html %}
{% raw %}
<button type="button" onclick="Ctesius.kickEvent('load_next_for_infinite_scroll');">
 Load more properties
</button>
{% endraw %}
{% endhighlight %}
<br>
**Hiding the button**

When there is no next page to load, you will want to hide the load more button. To do this, add the following event:

{% highlight javascript %}
{% raw %}
Ctesius.registerEvent('performed_next_infinite_scroll', function(a){
  if (!a.pagination.has_next_page){
    $('.your_button_class').hide();
  }
});
{% endraw %}
{% endhighlight %}