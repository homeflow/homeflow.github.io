---
layout: default
title: Send to Friend
modal-id: send-to-friend
category: property-show-page
---
Properties can be shared on the Homeflow platform. All you have to do is include the following snippet:

{% highlight liquid %}
{% raw %}
	{% include 'user/send_to_friend' %}
{% endraw %}
{% endhighlight %}

This will include the default send to friend colorbox modal code. This will work out of the box if you have included the Homeflow application.js in your layout. Alternatively if you want to override or customize this form, add a partial of is your user folder called ``_send_to_a_friend.liquid`` and add:

{% highlight html %}
{% raw %}

<div class="modal" id="send_to_friend_modal" style="display:none;">

 <div class="modal-header">
  <a class="close" data-dismiss="modal">×</a>
  <h3>Share '{{ property.road_name }}' with a friend</h3>
 </div>

 <div class="modal-body">
  <form action="/user/send_to_friend" method="post">
   <div class="control-group">
    <label class="text" for="mailer[from_name]">Your name</label>
    <input id="mailer[from_name]" name="mailer[from_name]" type="text">
    <label class="text" for="mailer[recipient_name]">Your friend's name</label>
    <input id="mailer[recipient_name]" name="mailer[recipient_name]" type="text">
   </div>
   <div class="control-group">
    <label class="text" for="mailer[from_email]">Your email</label>
    <input id="mailer[from_email]" name="mailer[from_email]" type="email">
    <label class="text" for="mailer[recipient_email]">Your friend's email</label>
    <input id="mailer[recipient_email]" name="mailer[recipient_email]" type="text">
   </div>
   <div class="control-group">
    <label class="text" for="mailer[message]">Message</label>
    <textarea id="mailer[message]" name="mailer[message]" rows="3"></textarea>
   </div>
   <input type="hidden" name="mailer[property_id]" value="{{ property.property_id }}">
   <input type="hidden" name="mailer[channel]" value="{{ current_channel }}">
   <div id="additionals">
    <input type="text" name="mailer[body]" value="" />
   </div>
   <div class="submit">
    <input name="submit" type="submit" value="SEND">
   </div>
  </form>
 </div>
</div>

{% endraw %}
{% endhighlight %}

<br />

Here is an example using Bootstrap's built-in CSS modal and form classes:

{% highlight html %}
{% raw %}
<div id="send_to_friend_modal" class="modal fade" tabindex="-1" role="dialog">
  <div class="modal-dialog">
    <div class="modal-content">
      <div class="modal-header">
        <button type="button" class="close" data-dismiss="modal" aria-hidden="true">×</button>
        <h2>Share '{{ property.road_name }}' with a friend</h2>
      </div>
      <div class="modal-body">
        <form action="/user/send_to_friend" method="post">
          <fieldset>
            <label for="mailer[from_name]">Your name</label>
            <div class="form-control-container">
              <input id="mailer[from_name]" name="mailer[from_name]" type="text" class="form-control">
            </div>
          </fieldset>

          <fieldset>
            <label for="mailer[recipient_name]">Your friend's name</label>
            <div class="form-control-container">
              <input id="mailer[recipient_name]" name="mailer[recipient_name]" type="text" class="form-control">
            </div>
          </fieldset>

          <fieldset>
            <label for="mailer[from_email]">Your email</label>
            <div class="form-control-container">
              <input id="mailer[from_email]" name="mailer[from_email]" type="email" class="form-control">
            </div>
          </fieldset>

          <fieldset>
            <label for="mailer[recipient_email]">Your friend's email</label>
            <div class="form-control-container">
              <input id="mailer[recipient_email]" name="mailer[recipient_email]" type="text" class="form-control">
            </div>
          </fieldset>

          <fieldset>
            <label for="mailer[message]">Message</label>
            <div class="form-control-container">
              <textarea id="mailer[message]" name="mailer[message]" rows="3" class="form-control"></textarea>
            </div>
          </fieldset>

          <input type="hidden" name="mailer[property_id]" value="{{ property.property_id }}">
          <input type="hidden" name="mailer[channel]" value="{{ current_channel }}">
          <div id="additionals">
            <input type="text" name="mailer[body]" value="" />
          </div>
          <button type="submit" class="btn btn-primary">Send</button>
        </form>
      </div>
    </div>
  </div>
</div>
{% endraw %}
{% endhighlight %}
