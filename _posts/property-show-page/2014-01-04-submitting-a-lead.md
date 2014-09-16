---
layout: default
title: Submitting a lead
modal-id: submitting-a-lead
categories: property-show-page
---
Email type leads are submitted to Homeflow and then on to the agent by ubiquitous web forms. Here's a simplified version:

{% highlight html %}
{% raw %}
<form action="/properties/{{property.property_id}}/{{property.primary_channel}}/leads" method="post">
 <div id='form_error'></div>
 <label class="text" for="firstname">First name</label>
  <input id="firstname" name="lead_client[first_name]" type="text">
 <label class="text" for="surname">Last name</label>
  <input id="surname" name="lead_client[last_name]" type="text">
 <label class="text" for="email">Email</label>
  <input id="email" name="lead_client[email]" type="email">
 <label class="text" for="telephone">Telephone</label>
  <input id="telephone" name="lead_client[tel_home]" type="text">
 <label class="text" for="message">Message</label>
  <textarea id="message" name="lead[message]" rows="3"></textarea>
 <button type="submit">Send enquiry</button>
</form>
{% endraw %}
{% endhighlight %}

If you are familiar with forms, which we're sure you are, there will be nothing new here to you. The only requirements are the names of the fields as well as the form action. The form error div near the top is reserved for any lead sending errors. Once a lead is sent, a ``flash message`` can be displayed. We have a whole array of flash notices that are used depending on the response back from the server and to display the notices, all you need to do is and the alert location div to your ``application.liquid`` or on the subject page itself:

{% highlight html %}
<div id='alert_location'></div>
{% endhighlight %}