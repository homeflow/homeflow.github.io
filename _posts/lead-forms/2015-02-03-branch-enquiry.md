---
layout: default
title: Submitting a branch enquiry lead
modal-id: submitting-a-branch-enquiry-lead
category: lead-forms
---
Branch enquiry leads are submitted using the following set of form elements. The HTML can be customised as needed:

{% highlight html %}
{% raw %}
<form action="/leads" method="post" class="contact_form branch_form" id="contact_form">
 <div id='form_error'></div>
 <input type="hidden" name="lead[branch_id]" value="{{branch.branch_id}}">
 <input type="hidden" name="lead[is_branch_lead]" value="1">
 <input id="firstname" class="required" name="lead_client[first_name]" type="text">
 <input id="surname" class="required" name="lead_client[last_name]" type="text">
 <input id="email" class="required" name="lead_client[email]" type="email">
 <input id="telephone" name="lead_client[tel_home]" type="text">
 <textarea id="message" name="lead[message]" rows="3"></textarea>
 <button id="contact_form_button" type="submit">Send message</button>
</form>
{% endraw %}
{% endhighlight %}

If you're constructing a form on a branch index page, or elsewhere, you can use a branch selector dropdown:

{% highlight html %}
{% raw %}
<select name="lead[branch_id]" tabindex="1">
 {% for branch in agency.branches %}
  <option value="{{ branch.branch_id }}">{{branch.name}}</option>
 {% endfor %}
</select>
{% endraw %}
{% endhighlight %}