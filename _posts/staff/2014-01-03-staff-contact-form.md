---
layout: default
title: Staff contact form
modal-id: staff-contact-form
category: staff
---
The Homeflow platform allows users to contact staff directly and leads are copied to the agency email address. Here's a sample form construct:

{% highlight html %}
{% raw %}
<form method="post" action="/leads">
 <input type="hidden" name="lead[agency_employee_id]" value="{{ staff_member.user_id }}">
 <h2>Contact {{staff_member.first_name}}</h2>
 <div class="left-col">
  <label>First Name <input name="lead_client[first_name]" type="text"></label>
  <label>Last Name <input name="lead_client[last_name]" type="text"></label>
  <label>Email <input name="lead_client[email]" type="text"></label>
  <label>Telephone <input name="lead_client[tel_home]" type="text"></label>
  <label>Message <textarea name="lead[message]"></textarea></label>
 </div>
 <div class="right-col">
  <label>Street Address <input type="text" name="lead_client[street_address]"/></label>
  <label>Town <input type="text" name="lead_client[town]"/></label>
  <label>County <input type="text" name="lead_client[county]"/></label>
  <label>Postcode <input name="lead_client[postcode]" type="text"></label>
  <input type="submit" value="Submit">
 </div>
</form>
{% endraw %}
{% endhighlight %}

Most of this is very standard form HTML, though note that the action, hidden ``employee_id/user_id`` and the names of the fields are super important. Without these the submission will fail.