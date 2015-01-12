---
layout: default
title: Send to Friend
modal-id: send-to-friend
category: property-functions
---

Properties can be shared on the Homeflow platform.  All you have to do is include the following snippet:

{% highlight liquid %}
	{% include 'user/send_to_friend' %}
{% endhighlight %}

This will include the send to friend colorbox modal code. This will work out of the box if you have included the Homeflow application.js in your layout. Alternatively if you want to override or customize this form you can see the example form in the stabilisers theme at ``https://github.com/homeflow/stabilisers/blob/master/includes/_send_to_friend.liquid``