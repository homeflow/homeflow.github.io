---
layout: default
title: Form fields
modal-id: custom-forms
category: custom-forms
---
We also allow file upload elements for custom forms (foolish perhaps?). These can be defined by picking an input with type "file" in the form fields section for a form in Logos.

For custom forms with attachments you will need to add enctype=”multipart/form-data” to the form tag like so:

{% highlight html %}
{% raw %}
<form class="my_class" action="/form_submissions" method="post" id="custom_form" enctype='multipart/form-data'>
{% endraw %}
{% endhighlight %}
