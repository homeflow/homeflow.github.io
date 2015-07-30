---
layout: default
title: Alternative page layouts
modal-id: alternative-page-layouts
category: cms-pages
---
Sometimes theme content managed pages are vastly different to one another. This makes constructing the layout tricky in the CMS, as well as in the page template itself. To get around this, Ctesius allows you to specify alternative templates for nominated pages.

Your first port of call is to add some directives to the YML file:

{% highlight yaml %}
 additional_layouts:
  - name: 'Tabbed'
  - name: 'Sell_Let'
  - name: 'Contact'
{% endhighlight %}

The backend CMS then reads this file and adds the templates to the page layouts dropdown at the foot of the edit page. Next, you need to add the template into the layout folder so it can be used. For the tabbed layout, we would have ``tabbed.liquid``. 

The only caveat with specifying alternative templates is that you have to build the page from scratch with any dependencies - much like the application.liquid file in many ways. Effectively you can just take a copy and include the custom section as an include. This is strongly recommended to make the page layout maintainable.