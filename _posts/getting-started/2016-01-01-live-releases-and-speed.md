---
layout: default
title: Live releases and speed
modal-id: live-releases-and-speed
category: getting-started
---
You will have the access to push any code to the staging server. Homeflow developers will primarily be using a different branch and server to push their changes so as not to conflict with the staging box. This box will run off the following URL:

``http://agency_homeflow_domain.dev.staging.homeflow.co.uk``

At suitable times during the build process it might be necessary to push the theme live to the production server. This is something that Homeflow will have to do manually due to the potential implications on other live sites.

### Server speed
It is important to note that the staging server has minimal caching on it and therefore it will run at noticeably slower speed than the production box. 
