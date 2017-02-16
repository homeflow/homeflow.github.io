---
layout: default
title: Article Drop
modal-id: article-drop
category: drops
---

Below are the methods available on the ArticleDrop, what they return and also what they expect to be passed when calling the method.

#### author
**Returns:** The [StaffMemberDrop](#staff-member-drop) of the Article author.

#### author_id
**Returns:** The id of the staff member who wrote the article.

#### article_id
**Returns:** The article's ID.

#### branch
**Returns:** The associated branch as a [BranchDrop](#branch-drop).

#### branch_id
**Returns:** The ID of the branch associated with the article.

#### canonical_url
**Returns:** The canonical_url for the article.

#### content
**Returns:** The Article content text.

#### created_at
**Returns:** The raw date/time the article was created.

#### date
**Returns:** The date the article was created, formatted.

#### hero_asset
**Returns:** A MrRichardImage of the article hero asset.

#### image
**Returns:** A MrRichardImage of the article main image.

#### meta_description
**Returns:** The article's meta title as a string.

#### meta_title
**Returns:** The article's meta title as a string.

#### month
**Returns:** The month the article was created.

#### promo
**Returns:** The article promo text content.

#### promo_image
**Returns:** A MrRichardImage of the article promo image, which could be used on list pages or the homepage.

#### slug
**Returns:** A string URL friendly link name for the Article.

#### title
**Returns:** The Article's title as a string.

#### topic
**Returns:** The topic of the Article as a string.

#### topics
**Returns:** An array of topics for the article if they are comma seperated.

#### year
**Returns:** The year the article was created.
