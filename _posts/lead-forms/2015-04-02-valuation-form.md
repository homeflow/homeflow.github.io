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