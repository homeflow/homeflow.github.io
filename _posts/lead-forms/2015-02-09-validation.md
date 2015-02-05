---
layout: default
title: Validation
modal-id: validation
category: lead-forms
---
Validation is super easy on the forms. Included in the application.js bundle is jquery.validate. You can add basic validation with the following snippet.


{% highlight javascript %} 
{% raw %}
$().ready(function() {
  $(".contact_form").validate({
    // Specify the validation rules
    rules: {
      first_name: "required",
      last_name: "required",
      email: {
        required: true,
        email: true
      }
    },

    // Specify the validation error messages
    messages: {
      first_name: "Please enter your firstname",
      lastn_ame: "Please enter your lastname",
      email: "Please enter a valid email address"
    }
  });

});
{% endraw %}
{% endhighlight %}