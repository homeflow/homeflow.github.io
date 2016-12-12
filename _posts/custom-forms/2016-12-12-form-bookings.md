---
layout: default
title: File uploads
modal-id: custom-forms
category: custom-forms
---
You can create form bookings using the custom forms field options. For example;

{% highlight html %}
{% raw %}

Friendly Name='Would you like to book a viewing?', Field Tag='input', Field Type='radio', Field Options='Yes|No'
Friendly Name='Booking Day', Field Tag='select', Field Type='string', Field Options='Monday|Tuesday|Wednesday|Thursday|Friday|Saturday|Sunday'
Friendly Name='Booking Time', Field Tag='select', Field Type='string', Field Options='09:00|10:00|11:00|12:00|13:00|14:00|15:00|16:00|17:00|18:00'

And these will render out like a normal form.
{% endraw %}
{% endhighlight %}
