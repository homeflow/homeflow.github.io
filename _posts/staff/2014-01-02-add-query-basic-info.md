---
layout: default
title: Add/query basic information
modal-id: query-basic-info
category: staff
---
Your first port of call before we can query any of the staff information is to add some. The Homeflow platform has hundreds if not thousands of profiles already loaded, so you might find we already have staff on record. That aside, log on to your agency admin and navigate to: ``/configure/business/staff``. From here follow the links to add/modify/remove staff as required.

Let's start with the staff index - the entry point that lists all staff members. This ``index.liquid`` file should live within a ``staff`` folder in your repository. A simple loop to retrieve all staff could be:

{% highlight html %}
{% raw %}
{% for profile in agency.staff_profiles %}
 <img src="{{ profile.avatar | url_for_staff_profile_avatar : "x97" }}" alt="{{ profile.name }}" width="97">
 <div>
  <h1>{{ profile.name }}, {{ profile.job_title }}</h1>
  <p>{{ profile.short_bio }}</p>
  <a href="{{profile | url_for_staff_member}}">Contact {{ profile.name }}</a>
 </div>
{% endfor %}
{% endraw %}
{% endhighlight %}

The next page you will want to create is the staff show page - ``show.liquid``. This page does not require any kind of loop and instead you can simply use the ``staff_member`` drop to access the information you require. Here's a typical construct you might come across:

{% highlight html %}
{% raw %}
<div class="span6">
 <h4>{{staff_member.name}}</h4>
 {% if staff_member.long_bio %}
  <p>
   {{staff_member.long_bio}}
  </p>
 {% endif %}
 <div class="social">
  {% if staff_member.facebook_uri %}
   <p>
    <a href="{{ staff_member.facebook_uri }}">
     <img src="{{ "facebook_50x50.png" | theme_image_url }}" width="21" height="21">
    </a>
   </p>
  {% endif %}
  {% if staff_member.twitter_uri %}
   <p>
    <a href="{{ staff_member.twitter_uri }}">
     <img src="{{ "twitter_50x50.png" | theme_image_url }}" width="21" height="21">
    </a>
   </p>
  {% endif %}
  {% if staff_member.linkedin_uri %}
   <p>
    <a href="{{ staff_member.linkedin_uri }}">
     <img src="{{ "linkedin_50x50.png" | theme_image_url }}" width="21" height="21">
    </a>
   </p>
  {% endif %}
 </div>
</div>
<div class="span6">
 {% if staff_member.avatar %}
  <img src="{{ staff_member.avatar | url_for_staff_profile_avatar : "300x_" }}" /> 
 {% else %}
  <img src="{{ 'silhouette.png' | theme_image_url}}">
 {% endif %}
</div>
{% endraw %}
{% endhighlight %}

Notice here we've introduced the ``long_bio``, social icons and links such as ``staff_member.linkedin_uri``, and an avatar drop with a backup silhouette output should we not have an avatar for the staff member. Checkout the [Other staff drops](/appendix/#other-staff-drops) section in the appendix for more available fields.


