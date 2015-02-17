---
layout: default
title: The navigation menu
modal-id: navigation-menu
category: application-and-homepage
---
Let's assume for now you would like to query the agency admin and therefore Hestia for the menu and, if it has been added, its sub-menu counterpart.

To start head over to your agency admin. Reminder: ``http://agency_homeflow_domain.homeflow.co.uk/admin``

Then go to ``Website/Navigation``. From here you can drag in menu items for existing pages or create custom links, e.g. to the ``/branches`` page for example. Once you've got your primary menu items, you can then edit each one and add sub-menu items.

Here's a code construct that would retrieve the primary menu items:

{% highlight html %}
{% raw %}
{% assign primary_menu = 'primary' | site_menu %}
<ul class="top-level">
 {% for menu_item in primary_menu.items %}
  <li class="top-level-li">
   <a href="{{ menu_item.url }}">{{ menu_item.name }}</a>
  </li>
 {% endfor %}
</ul>
{% endraw %}
{% endhighlight %}

So what about a nested menu to support dropdrowns? Here's a code construct that will satisfy this requirement:

{% highlight html %}
{% raw %}
<ul class="top-level">
 {% assign primary_menu = 'primary' | site_menu %}
 {% for menu_item in primary_menu.items %}
  <li class="top-level-li">
   <a class="navigation" href="{{ menu_item.url }}">{{ menu_item.name }}</a>
   {% if menu_item.items != empty %}
    <ul class="subnav">
     {% for sub_menu_item in menu_item.items %}
      <li>
       <a href="{{sub_menu_item.url}}">{{sub_menu_item.name }}</a>
      </li>
     {% endfor %}
    </ul>
   {% endif %}
  </li>
 {% endfor %}
</ul>
{% endraw %}
{% endhighlight %}

###Highlighting the active link

The typical way to achieve this is to assign a category to your menu items and pages via the agency admin. Within your navigation loop, if the page category matches the menu item's category, then you can add the active:

{% highlight html %}
{% raw %}
<a href="{{menu_item.url}}" {% if menu_item.category == page.category %}class="active"{% endif %}>
{% endraw %}
{% endhighlight %}