---
layout: default
title: Flash messages
modal-id: flash-messages
category: application-and-homepage
---
Flash messages are used to provide feedback to the user after some event. Flash messages include lead send success or failures, user registrations, valuation leads sent and so on.

In its basic form, you have an empty div ready to be populated with a message:

{% highlight html %}

<div id='alert_location'></div>

{% endhighlight %}

An event and callback function is then registered to populate the container:

{% highlight javascript %}

Ctesius.registerEvent('redirection_flash_ready', function(message, type){
 var mess = '<div class="alert alert-'+type+'">
            <a class="close" data-dismiss="alert">×</a>'+message+'</div>'
 $('#alert_location').html(mess)
});

{% endhighlight %}

Note that you have access to the message contents and type, as well as full control over the position of the div, its styling and behaviour.