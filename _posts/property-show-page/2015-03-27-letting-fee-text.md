---
layout: default
title: Letting fee text
modal-id: letting-fees
category: property-show-page
---
Developers have complete control of the text and rendering of the notification to the user. Here's one such example of how we accomplished it using Bootstrap modal.

Firstly on the results page and the show page, a good practice is to check the channel before outputting the modal block:

{% highlight liquid %}
{% raw %}
{% if current_channel.name == 'lettings' %}
 <div id="fees" class="modal fade" role="dialog">
  <div class="modal-header">
   <button type="button" class="close" data-dismiss="modal">&times;</button>
   <h4 class="modal-title">Fees Apply</h4>
  </div>
  <p>
   {% content_block fee_text %}
    {{content_block}}
   {% endcontent_block %}
  </p>
 </div>
{% endif %}
{% endraw %}
{% endhighlight %}

You will have noted here that we're using a content block to manage the text of the fees popup - this makes sense, since the wording will vary from agent to agent.

For each property record on the results page and on the show page, you would add something like the following to highlight that fees apply and to let the user click to reveal the modal:

{% highlight liquid %}
{% raw %}
{% if property.primary_channel == 'lettings' %}
 <a class="fees" data-toggle="modal" data-target="#fees">* Fees Apply</a>
{% endif %}
{% endraw %}
{% endhighlight %}
