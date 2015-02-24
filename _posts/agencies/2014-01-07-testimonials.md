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

One more useful testimonials function is to assign a random testimonial and output to a given area:

{% highlight liquid %}
{% raw %}
{% assign testimonial = agency.featured_testimonial %}
<p>
 "{{testimonial.content}}"
 <span class="author">{{testimonial.name}}</span>
</p>
{% endraw %}
{% endhighlight %}