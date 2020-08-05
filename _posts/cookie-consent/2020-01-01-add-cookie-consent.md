---
layout: default
title: Add cookie consent
modal-id: add-cookie-consent
category: cookie-consent
---
To add the cookie consent popup to a theme, follow these steps.

If a theme already contains the include for the `cookie_directive` partial, remove it:

{% highlight liquid %}
  {% raw %}
    {% include 'layouts/cookie_directive' %} <-- remove this
  {% endraw %}
{% endhighlight %}

Add `cookie_consent` to both the theme’s vendor javascripts and stylesheets sections of config.yml (make sure you add the javascript pack after the ctesius and `asset_pack` theme scripts, and the stylesheet pack before `asset_pack`):

  {% highlight liquid %}
    {% raw %}
      vendor_assets:
          javascripts:
            - ctesius
            - asset_pack
            - cookie_consent
          stylesheets:
            - ctesius
            - cookie_consent
            - asset_pack
    {% endraw %}
  {% endhighlight %}

Add `{{ head_analytics_code }}` to the themes <head> (be sure to remove `{{ agency.preferences.head_analytics_code }}` if this is already in the theme!)

 
Add `{{ analytics_code }}` to the bottom of the body element (and remove `{{ agency.preferences.analytics_code }}` if this already exists).


The cookie consent code assumes that all third-party scripts will be coming from `head_analytics_code` and `analytics_code` from the agency’s admin preferences, therefore you should search the theme for any hardcoded third-party scripts or content blocks that may include third party scripts (like a `google_tag_manager` content block) and move the code into the analytics sections of the agent’s admin, e.g. [https://a1propertyuk.homeflow.co.uk/configure/website/appearance/preferences](https://a1propertyuk.homeflow.co.uk/configure/website/appearance/preferences)


To customise the cookie consent popup, use the wizard on this page to configure: [https://www.osano.com/cookieconsent/download/](https://www.osano.com/cookieconsent/download/) then carefully copy the configuration object (the thing inside parentheses that starts with `{` and ends with `}` - do not copy everything!) from inside the provided code and put it inside a content chunk named `cookie_consent_config` - be careful not to introduce any syntax errors as the content must be a valid JavaScript object.

The content of the content chunk might look like this:

  {% highlight liquid %}
    {% raw %}
      {
        "palette": {
          "popup": {
            "background": "#000"
          },
          "button": {
            "background": "#f1d600"
          }
        },
        "position": "bottom-left",
        "type": "opt-in",
        "content": {
          "message": "This website uses cookies to give you the best experience.",
          "href": "/pages/cookie-policy"
        }
      }
    {% endraw %}
  {% endhighlight %}

This is the default if no content chunk is set (in case you only want to customise parts) - this uses Liquid to make the colours dynamic:


  {% highlight liquid %}
    {% raw %}
      {
        "palette": {
          "popup": {
            "background": "#edeff5",
            "text": "#838391"
          },
          "button": {
            "background": "transparent",
            "text": "{{ theme_preferences.button_tint_colour }}",
            "border": "{{ theme_preferences.button_tint_colour }}"
          },
        },
        "position": "bottom-left",
        "type": "opt-in",
        "content": {
            "href": "/pages/cookie-policy",
            "message": "This website uses cookies to give you the best experience.",
        }
      }
    {% endraw %}
  {% endhighlight %}

You can also HIDE the cookie completely by pasting this JSON into the above content chunk:

`{ "do_not_show": true }`

If you want to cookie popup to appear in the middle of the screen, with a grey background blocking the user from interacting with the page until they have accepted or declined cookies, add `"theme":` `"fullscreen"` to the object, e.g. 

  {% highlight liquid %}
    {% raw %}
      {
        "theme": "fullscreen",
        "palette": {
        ...etc
    {% endraw %}
  {% endhighlight %}

For any page specific third-party scripts that are hard coded within the theme, wrap the script using the following if statement in liquid:

{% highlight liquid %}
  {% raw %}
    {
    {% if cookies_accepted %}
      
    {% endif %}
  {% endraw %}
{% endhighlight %}
