---
layout: default
title: Saving Properties
modal-id: saving-properties
category: events
---
The following events will be kicked when a saved property is added or removed. The `by_action` events signify that the user has saved a property where it was not previously saved - these events are useful for displaying a flash message or a subtle animation. Without the `by_action`, the event should be used to decorate saved properties or remove descorating. For instance, changing text from 'Save property' to 'Remove property':

- ``before_saved_property_removed_by_action(property)``
- ``after_saved_property_added_by_action(property)``
- ``saved_property_added(property)``
- ``saved_property_removed(property)``

The following methods will be called if a saved properties list is rendered:

- ``saved_properties_view_rendered``
- ``saved_property_view_rendered(property)``