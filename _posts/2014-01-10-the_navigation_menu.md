---
layout: default
title: The navigation menu
modal-id: the-navigation-menu
---
The navigation is another area where you have complete freedom of development - if you wanted to hardcode your menu and add/remove new or old items as they come along, that's absolutely fine. If however, you'd prefer to add the navigation tree to the agency admin and extract them using Liquid, that's fine too. Generally speaking portals add their menu to their source whereas theme designers or agency sites will tend to code the menu using Liquid, as their theme can then be deployed for multiple agencies.

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

Here we can see two new things: an ``assign`` statement and a Liquid ``for loop ``.

The ``assign`` statement allows you to assign something to a Liquid variable. This can be as simple as a string or result of some evaluation. Also, as seen above, you can assign Liquid objects to a variable for looping and other purposes.

And the good old ``for loop``. You'll probably be familiar with the ``for loop`` from other programming languages and Liquid's variant is very simple to use - loop through an object and you can write out its attributes as required.

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

There's nothing new here but let's step through what's going on. Firstly we do our ``assign`` then we loop through the ``primary menu items`` and output an ``li`` and ``anchor`` for each. Next we check whether the menu item we're looping over has any items within it by doing an ``if not empty`` test - ``empty`` is a handy Liquid check to see if a variable has been initialised. If so, we output another unordered list and then we loop through the sub menu items of that menu item. We then output an ``li`` and ``anchor`` for each.

Finally we close off the ``if`` and ``for loop`` using the appropriate end Liquid statements.