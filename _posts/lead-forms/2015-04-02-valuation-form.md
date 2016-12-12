---
layout: default
title: Valuation form
modal-id: valuation-form
category: lead-forms
---
Like the register form seen above, a valuation request is a lead type in itself. It also shares the same fields as the register form, the only differences are the form directives and one or two hidden fields so that the request hits the correct controller in the Ctesius app. In addition, the valuation form needs to live in a ``/pages/request_valuation.liquid`` file.

Review the [register form](/cms-pages/#register-form) for the form fields and amend the form head as follows to get up and running:

{% highlight html %}
{% raw %}

<form action="/leads" method="post" id="contact_form">
 <input type="hidden" name="lead[is_valuation_request]" value="1"/>
 <input type="hidden" value="{{agency.agency_id}}" name="lead_client[agency_id]">      

 ... other form fields

</form>

{% endraw %}           
{% endhighlight %}

You can also add client bookings to your valuation lead forms,

{% highlight html %}
{% raw %}

<label>Would you like to book a viewing?</label>

<label for="lead_booking[book_viewing]">Yes</label>
<input id="book_viweing" type="radio" value="yes" name="lead_booking[book_viewing]">

<label for="lead_booking[book_viewing]">No</label>
<input id="book_viweing" type="radio" value="no" name="lead_booking[book_viewing]">

<label class="text" for="lead_booking[booking_time]">Time</label>
<input id="lead_booking[booking_time]" name="lead_booking[booking_time]" type="text">

<label class="text" for="lead_booking[booking_day]">Day</label>
<input id="lead_booking[booking_day]" name="lead_booking[booking_day]" type="text">

<label class="text" for="lead[booking_month]">Month</label>
<input id="lead_booking[booking_month]" name="lead_booking[booking_month]" type="text">

<label class="text" for="lead[booking_year]">Year</label>
<input id="lead_booking[booking_year]" name="lead_booking[booking_year]" type="text">
{% endraw %}           

{% endhighlight %}
