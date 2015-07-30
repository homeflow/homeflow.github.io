---
layout: default
title: Alternative user profile tech
modal-id: alternative-profile-tech
category: user-profile-system
---
As mentioned before, Colorbox is used by default. For rapid development, the default templates and Colorbox do just fine. If however, you wish to use alternative tech like Bootstrap modal, or some other responsive modal system, here's how:

Firstly we need to define our modal container. If it was Bootstrap modal, it might look something like the code below (we've stripped some HTML for simplicity):

{% highlight html %}
{% raw %}
<div id="user_profile" class="modal fade modal-lg" role="dialog">
 <div class="modal-dialog">
  <div class="modal-content">
   <div class="modal-body" id="profile-content"></div>
  </div>
 </div>
</div>
{% endraw %}
{% endhighlight %}

Then we need to define a couple of events. The first is ``user_view_render_handler_render``. This will be kicked any time the user box needs show or update itself. This can happen multiple times during page load:

{% highlight javascript %}
{% raw %}
Ctesius.registerEvent('user_view_render_handler_render', function(html, user, id){
 $('#profile-content').html(html)
 $('#user_profile').modal('show');
});
{% endraw %}
{% endhighlight %}

When the profile system needs to close (e.g the user has logged out), this event will be fired:

{% highlight javascript %}
{% raw %}
Ctesius.registerEvent('user_view_render_handler_close', function(html, user, id){
 $('#profile-content').html('')
 $('#user_profile').modal('hide');
});
{% endraw %}
{% endhighlight %}

As you can see, if you elect to use alternative profile tech, you must make sure the HTML gets appended, as well show and hide the modal when required.

