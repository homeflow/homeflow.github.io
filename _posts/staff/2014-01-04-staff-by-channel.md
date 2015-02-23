---
layout: default
title: Staff by channel
modal-id: staff-by-channel
category: staff
---
Say you want to extract some or all sales staff on sales properties and the same for lettings. Here's how you can do just that:

{% highlight liquid %}
{% raw %}
{% if current_channel.name == 'sales' %}
    {% assign staff_profiles = branch.staff_profiles
    | selected_by : 'contactable_for_sales', true %}
{% endif %}

{% if current_channel.name == 'lettings' %}
    {% assign staff_profiles = branch.staff_profiles
    | selected_by : 'contactable_for_lettings', true %}
{% endif %}
{% endraw %}
{% endhighlight %}

{% highlight html %}
{% raw %}
{% if staff_profiles %}
 <h3>Meet the team</h3>  
 <ul class="thumbnails">
  {% for staff in staff_profiles limit: 3 %}
   <li>
    <a href="{{ staff | url_for_staff_member }}">
     <img src="{{staff.avatar | url_for_generic_image }}" alt="{{staff.name}}" />
    </a>
    <h4>{{staff.name}}</h4>
    <p>{{staff.short_bio | truncate : 125}}</p>
    <a href="{{ staff | url_for_staff_member }}">Full profile</a>
   </li>
  {% endfor %}
 </ul> 
 <a href="/staff" class="button">Meet the whole team</a>
{% endif %}
{% endraw %}
{% endhighlight %}

Tip: the ``selected_by`` code seen above can be used to filter an array based on an attribute of an object. ``contactable_for_sales`` is a true or false attribute we can use to filter staff, depending on the property's channel.