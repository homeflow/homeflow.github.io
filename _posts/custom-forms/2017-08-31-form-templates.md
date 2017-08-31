---
layout: default
title: Form Templates
modal-id: custom-forms
category: custom-forms
---


Here is an example of a formatted custom form.

<img style="width: 75%" src="/../img/custom_form_no1.png">

If you would like to use this form please refer to the code linked <a href="/form_templates" target="_blank">Here.</a>

Once the text has been copied and pasted into a new content_block named "contact_us_form", It can then be called in the source code of the required page.

{% highlight html %}
{% raw %}
  {% content_block contact_us_form %}
    {% if content_block %}
      {{content_block}}
    {% endif %}
  {% endcontent_block %}
{% endraw %}
{% endhighlight %} 


Remember to change the value of the first input to the custom form ID number that is generated when the form is created in logos(i.e 289), and to change the second inputs value to the necessary Url (i.e /test). 

{% highlight html %}
{% raw %}
<form action="/form_submissions" class="enquiry-form" id="contact_form" method="post">
	<input name="f_id" type="hidden" value="{ custom form ID }" /> 
	<input id="hidden-redirect-url" name="redirect_url" type="hidden" value="{ url for testing page }"/>
{% endraw %}
{% endhighlight %}


To change any  of the forms styles simply add a class to the parent element and add the  prefered styles within the pages custom css. 