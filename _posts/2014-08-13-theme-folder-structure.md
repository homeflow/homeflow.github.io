---
layout: default
title: Theme folder structure
modal-id: 3
---
Ctesius themes use the standard Rails conventions for folder layouts. Don't worry if you're not familiar with Rails or this structure as an example theme folder structure can be seen below or found on the demo Stabilisers theme.

{% highlight html %}
theme_name
    agencies
        index.liquid
        show.liquid
    articles
        index.liquid
        show.liquid
    assets
        images
        javascripts
        stylesheets
            theme_styles.lcss - our LCSS file holds our styles just like a CSS file
    branches
        _branches_list.ljson - a JSON view to list an array of branches
        index.liquid
        show.liquid
    home
        home.liquid - the main homepage
    layouts
        application.liquid - the main layout file which renders the other pages
    pages
        show.liquid
    properties
        _properties_list.ljson - a JSON view to list an array of properties
        index.liquid
        show.liquid
    staff
        index.liquid
        show.liquid
    user
        new.liquid
{% endhighlight %}

If your repository doesn't have these files and folders yet, add them in. Once done, make your first commit and push to your repository. We would recommend a Git GUI such as Tower for OSx or one of the freebies available for Linux such as Git Cola. If you're using Git via the command line, bring up a terminal, cd to you theme's root directory and run:

{% highlight html %}
    git commit -a -m 'Theme folders and files'
{% endhighlight %}

Then run:

{% highlight html %}
    git push origin master
{% endhighlight %}

This will add all of your modified files, commit them as well as push them to the remote repository. We can't view the site online just yet as there's nothing to render. Time to add some structure and content to our application.liquid file.