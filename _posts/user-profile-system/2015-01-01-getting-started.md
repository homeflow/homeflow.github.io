---
layout: default
title: Getting started
modal-id: getting-started
category: user-profile-system
---
####Saved Properties

To render the saved properties block in a particular place, simply create a div with an ID of `saved_properties_view`. 

{% highlight html %}
	<div id="saved_properties_view" class="hidden"></div>
{% endhighlight %}

This tells the liquid that the view is to be rendered here. The next step is to include the defualt `js_templates` partials which contain the standard HTML for the blocks to be rendered.

{% highlight html %}
	{% raw %}
   		{% include 'layouts/js_templates' %}
   	{% endraw %}
{% endhighlight %}

You can override this HTML by adding your own `saved_properties_view` and `favourite_properties_template` somewhere in your layout - eg.  
{% highlight html %}
	{% raw %}
	  <script id="saved_properties_template" type="text/liquid">
		  <div id="property_shortlist" class="content-block">
			  <h2>My property shortlist</h2>
			  <div id='favourite_property_list' class="content">
	
			  </div>
		  </div>
	  </script>

	  <script id="saved_property_template" type="text/liquid">
	    <div id="mini_property_{{property.property_id}}" class="mini_property mini_property_{{property.property_id}}" style="">
	      <div style="position:relative;" class="clearfix">
	        <img src="/liquid_assets/images/delete.png" id="remove_icon_{{property.property_id}}" class="remove_icon" onclick="javascript:Ctesius.Actions.removeSavedProperty({{property.property_id}})">
	        <a href="{{property.property_url}}"><img src="{{ property.small_photo }}"></a>
	        <div class="featured_property_data">
	          <ul>
	            <li><a href="{{property.property_url}}">{{ property.bedrooms }} bedrooms</a></li>
	            <li><a href="{{property.property_url}}">{{ property.price }}</a></li>
	            <li><a href="{{property.property_url}}">{{ property.road_name }}</a></li>
	          </ul>
	        </div>
	      </div>
	    </div>
	  </script>
	{% endraw %}
{% endhighlight %}


You can also override each of the views that the JS renders by default by creating the following files in your app.

- js_templates/_profile_user_info.liquid
- js_templates/_account.liquid
- js_templates/_profile_saved_properties.liquid
- js_templates/_profile_saved_searches.liquid

Events can also be registered in javascript using the Ctesius event system to give visual feedback or other front end calls when saving a property, as detailed below.

####Associated Events
There are a bunch of callbacks that are fired when events take place in Ctesius system. This enabled you to wrap any scripts or HTML within these to provide feedback for these events. Below is a list of these events:

 - **saved_property_view_rendered** Fired when a saved property has been added.
  - **saved_property_removed** Fired when a saved property has been removed.
  - **saved_search_added** Fired when a search is saved to the users favourites.
  - **saved_search_removed** Fired when a saved search is removed.
  
Here is an example of the 'saved_property_view_rendered' callback being used:

{% highlight javascript %}

	Ctesius.registerEvent('saved_property_view_rendered', 
		function(saved_property){
			$('#saved_properties_view').removeClass("hidden");
			$("#add_to_shortlist_"+saved_property.id).html("Remove from Shortlist");
	});
{% endhighlight %}

####Modal vs Non-modal

The above example gives the user a non modal feedback that they have saved properties. There is also the modal view where the whole profile system resides. A user can view their saved properties directly in the modal view by appending /#user/saved_properties to any URL within the site. 

Linking to the modal windows are quite simple. 


	href="#/user"


Is all thats needed for the user profile box to load. Similarly `/#/user/saved_properties` and `/#/user/saved_searches` are required for the other tabs respectivly. 

####Saved Searches

Saved searches work in a similar way but are even more simple. Simply add a link to `Ctesius.Actions.saveCurrentSearch()` on a results page and this should be all thats required. 


####Associated Events
To override any default callabacks simply override the following Ctesius events. 

 - **saved_search_added**
 - **saved_search_removed**


A user can view their saved properties directly by appending /#user/alerts to any URL within the site. 

####User micro view
The user micro view can be used to display the current user state, whether logged in or not, as well as favourite counts etc. To use this, simply add the following div to the site.

{% highlight html %}
	<div id="user_micro_view"></div>
{% endhighlight %}


####Accountless vs Logged in

Homeflow offers both accountless saving of searches and properties as well as logged in versions. When a user registers or logs in whilst having accountless searches or properties - they are syncronised with the existing data at the login. 

####Modal Customization

You can customize the main profile system that is contained in the modal view creating the following partials in your theme and therefore overriding the default partials.

   **/js_templates/_profile_account.liquid**
   **/js_templates/_saved_properties.liquid**
   **/js_templates/_saved_searches.liquid**
