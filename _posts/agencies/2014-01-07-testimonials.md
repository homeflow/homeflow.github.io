---
layout: default
title: Testimonials
modal-id: testimonials
category: agencies
---
Agency testimonials can be added via the CMS link: ``/configure/website/testimonials``. You can then loop over and output the testimonials as follows:

{% highlight liquid %}
{% raw %}
{% for testimonial in agency.testimonials limit: 20 %}
 <blockquote>
  <p>"{{ testimonial.content }}"</p>
  <p>{{ testimonial.name }}</p>
 </blockquote>
{% endfor %}
{% endraw %}
{% endhighlight %}

A route exists in the Ctesius app the ``/pages/testimonials`` and a ``testimonials.liquid`` page can exist under your pages folder to have a dedicated testimonials page. Use the loop above here to extract them to the page.

A useful testimonials function is to assign a random testimonial and output to a given area:

{% highlight liquid %}
{% raw %}
{% assign testimonial = agency.featured_testimonial %}
<p>
 "{{testimonial.content}}"
 <span class="author">{{testimonial.name}}</span>
</p>
{% endraw %}
{% endhighlight %}

Need to slice the testimonials array to get the latest five and then shuffle them? Use the ``slice_array`` and ``shuffle`` functions:

{% highlight liquid %}
{% raw %}
{% assign testimonials = agency.testimonials | slice_array : 0, 4 %}
{% assign shuffled_testimonials = testimonials | shuffle %}

{% for testimonial in shuffled_testimonials limit: 1 %}
 <p>{{testimonial.content}}</p>
 <span class="author">{{testimonial.name}}</span>
{% endfor %}
{% endraw %}
{% endhighlight %}

Need testimonials by channel? No problem:

{% highlight liquid %}
{% raw %}
{% assign testimonials = agency.testimonials | selected_by : 'channel', 'lettings' %}

{% assign testimonials = agency.testimonials | selected_by : 'channel', 'sales' %}
{% endraw %}
{% endhighlight %}

Then loop through them as normal.
