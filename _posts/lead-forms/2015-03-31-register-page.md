---
layout: default
title: Register form
modal-id: register-form
category: lead-forms
---
The Ctesius app allows you to register new users to an agency. The standard URL to get to the page is ``/register`` and the registration form needs to live in a ``new.liquid`` file within a ``user`` folder. There are many fields you can use to request information from the client, though name, email and password are absolutely required:

{% highlight html %}
{% raw %}

<form action="/user" method="post">

 <input type="hidden" value="{{agency.agency_id}}" name="client[agency_id]">                    
 <div id='form_error'></div>
                         
 <label class="text" for="client[first_name]">First name</label>
  <input id="client[first_name]" name="client[first_name]" type="text">

 <label class="text" for="client[last_name]">Last name</label>
  <input id="client[last_name]" name="client[last_name]" type="text">

 <label class="text" for="client[email]">Email</label>
  <input id="client[email]" name="client[email]" type="email">

 <label class="text" for="client[password]">Password</label>
  <input id="client[password]" name="client[password]" type="password">

 <label class="text" for="client[password_confirmation]">Confirm password</label>
  <input id="client[password_confirmation]" type="password" name='client[password_confirmation]'>

 <label class="text" for="client[street_address]">Street</label>
  <input id="client[street_address]" name="client[street_address]" type="text">

 <label class="text" for="client[town]">Town</label>
  <input id="client[town]" name="client[town]" type="text">

 <label class="text" for="client[county]">County</label>
  <input id="client[county]" name="client[county]" type="text">

 <label class="text" for="client[postcode]">Postcode</label>
  <input id="client[postcode]" name="client[postcode]" type="text">

 <label class="text" for="client[tel_mobile]">Mobile</label>
  <input id="client[tel_mobile]" name="client[tel_mobile]" type="text">

 <label class="text" for="client[tel_home]">Home Telephone</label>
  <input id="client[tel_home]" name="client[tel_home]" type="text">
                   
{% endraw %}           
{% endhighlight %}      

Optionally, you can grab their requirements:

{% highlight html %}
{% raw %}

 <h3>Your Requirements:</h3>

 <input id="client[is_sales_applicant_at]" name="client[is_sales_applicant_at]" type="checkbox" checked="checked">
  <label class="check" for="client[is_sales_applicant_at]">I am looking to buy</label>

 <input id="client[is_lettings_applicant_at]" name="client[is_lettings_applicant_at]" type="checkbox">
  <label class="check" for="client[is_lettings_applicant_at]">I am looking to rent</label>

 <input id="client[is_vendor_at]" name="client[is_vendor_at]" type="checkbox">
  <label class="check" for="client[is_vendor_at]">I have a property to sell</label>

 <input id="client[is_landlord_at]" name="client[is_landlord_at]" type="checkbox">
  <label class="check" for="client[is_landlord_at]">I have a property to let</label>

 <label for="lead[message]">Comments</label>
  <textarea id="message" name="lead[message]"></textarea>

 <button type="submit">Send to {{agency.name}}</button>

</form>
             
{% endraw %}           
{% endhighlight %}    

On submit, be in that the lead has sent successfully has failed, the user will get redirected to a flash message, which will populate in the div container. Read more about [flash messages](/application-and-homepage/#flash-messages).
