---
layout: default
title: Custom Flash Messages
modal-id: custom-flash-messages
category: theme-config-options
---

On form submissions, successful or other, the browser will display a modal pop-up with
a default message. The content is customisable, using the following example as
a model:

{% highlight html %}
{% raw %}
<script>
$(document).ready(function(){
  Ctesius.addConfig('name-of-the-flash-message-to-override', 'your_custom_message');
});
</script>
{% endraw %}
{% endhighlight %}

This should typically be added to your 'js_event_registers.liquid' file, although
they can be added to a specific page where needed. 

If your theme is not bespoke, then 'your_custom_message' should be replaced with
a content block so that future users of the theme can add custom content.

Another example:

{% highlight html %}
{% raw %}
<script>
$(document).ready(function(){
Ctesius.addConfig('flash-message-welcome-lead-sent', 'Thank you for applying for the {{ article.slug | remove: "current-opportunities-""  }}' +
' position. You will have received a confirmation of your application and will hear from us if successful.' );
});
</script>
{% endraw %}
{% endhighlight %}

This would output:

{% highlight html %}
{% raw %}
Thank you for applying for the generic office position. You will have received a
confirmation of your application and will hear from us if successful.
{% endraw %}
{% endhighlight %}

Here is a list of flash message types, and the default messages which can be overriden:

- 'flash-message-welcome-lead-sent-new-user': "Thank you. We have sent your message and created - you an account."
- 'flash-message-welcome-lead-sent': "Thank you. We have sent your message."
- 'flash-message-lead-sending-error': "There was an error sending your message - please try again later."
- 'flash-message-file-upload-error': "There was an error uploading your attachment - please try again in a minute."
- 'flash-message-location-not-found': "Sorry, we couldn't find that location."
- flash-message-lead-sending-error-validation : "Sorry, we couldn't create your lead. Only alphanumeric characters are allowed for First and Last name."
- 'flash-message-send-property-sent': "This property has been shared successfully!"
- 'flash-message-send-property-invalid' : "There was an error trying to share this property."
- 'flash-message-user-create-dupe': "There is already a user with that email address registered."
- 'flash-message-user-create-successful': "You have registered successfully and been logged in."
- 'flash-message-user-login-successful': "You have been logged in successfully!"
- 'flash-message-user-create-error': "There was an error in registering you with the agent."
- 'flash-message-search-query-required': "Please enter a search query."
- 'flash-message-article-not-found-error': "Sorry, we could not find this article"
- 'flash-message-recaptcha-invalid': "The recaptcha you entered is not correct. Please try again."
- 'flash-message-invalid-message-content': "Your message contains illegal content. Please submit again."
- 'flash-message-password-invalid': "The password you have specified is invalid. Make sure it is alphanumeric and contains more than 5 characters."
- 'flash-message-postcode-invalid': "The postcode supplied seems to be invalid. Please try again"
- 'flash-message-site-not-live' : "<span>This website needs to be activated. Please contact Homeflow.</span>"
