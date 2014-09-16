---
layout: default
title: The branches index
modal-id: branches-index
categories: working-with-branches
---
As we saw with the ``properties index``, our index pages are called when no seach criteria is given and we just want a flat list of all properties, branches, etc. A branches index route would simply be: ``http://www.agency_domain.com/branches``. On our index page we can add the following code:

{% highlight html %}
{% raw %}
{% if branches != empty %}
 {% for branch in branches %}
  {% include "branches/branch_small" %}
 {% endfor %}
{% endif %}
{% endraw %}
{% endhighlight %}

This construct is exactly the same as a properties loop seen before except we are referencing our branches collection as well as including a ``branch_small`` partial for each returned branch. A ``branch_small`` might look something like:

{% highlight html %}
{% raw %}
<div class="branch">
 {% if branch.agency.portal_logo %}
  <img src="{{ branch.agency.portal_logo | url_for_agency_logo : "150!" }}" />
 {% else %}
  <img src="{{ 'awaiting-image.png' | theme_image_url }}" />
 {% endif %}
 <div class="details">
  <h3>
   <a href="{{ branch | url_for_branch}}">{{branch.name}} branch</a>
  </h3>
  <p class="content">
   {{branch.description | strip_tags | truncate : 250}}
  </p>
  <p>
   <a href="{{ branch | url_for_branch}}">More Information</a>
  </p>
 </div>
</div>
{% endraw %}
{% endhighlight %}

Here we are checking whether the agency's portal logo has been set and if it has, we output it in the source. Note you could use ``{% raw %}{{ branch.photo | url_for_generic_image: "150!" }}{% endraw %}`` instead, which would retrieve the branch photo as set in the branches area of the agency or portal admin. This photo is normally a shop front image or something similar. As another alternative, you could use the overall agency logo: ``{% raw %}{{ agency.logo | url_for_agency_logo : '150!'}}{% endraw %}``. Note that we've got a backup coded in to output a standard holding image if no portal logo is available. This is a ``theme_image_url`` - you may remember theme images reside in ``/assets/images``.

One new element here is the bang (explanation mark) after the width dimension. We've built in some nifty Liquid filters that give you some flexiblity when requesting images from the server. In this instance we're saying: get us the agency portal logo and resize it so the width and height are no more than 150 pixels. Other options here are to specify the dimensions exactly or specify a height or a width, then get Liquid to automatically set the other dimension whilst retaining the aspect ratio - we do this by using an underscore where the dimension you want to calculate would normally be, e.g: "150x_".

Next we're outputting the branch name and wrapping it in the URL for the branch. We then go on to output the branch description. Note that in some instances you might be able to guarantee that the description has been added, if you can't then you can wrap the output in an ``{% raw %}{% if branch.description }}{% endraw %}``. Note the truncate filter that we've seen before. There's also a new filter here called ``strip_tags``. Along with ``strip_html`` and ``strip_links`` it strips the description of any unwanted HTML tags and links.

Not every theme will call for a ``branch_small`` partial to be used - some might just have the name of the branch and a link, whilst others might have the name, link and a map of the branches.