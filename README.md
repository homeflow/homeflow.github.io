Homeflow API Theme
=========================

## Querying pages and posts

Each page has its own folder and index.html. Within this there is some Markdown that tells Jekyll the template to use. We also set 
some page attributes. More often than not the section template is called (/layouts/section.html). This template loops through 
posts, using the category attribute of the page to find the appropriate cateogory within the _posts folder. Note that the post 
folder names (known as categories to Jekyll) match the page category in the Markdown - this is so we query the correct posts.

## The sidebar

The sidebar works a little differently. It uses some well defined sections in the _config.yml. You'll note that the section
IDs match the page folder names - Jekyll uses the folder names for the URLs. The YAML file also allows us to set other
useful section info, such as if it has a sub menu.

The actual sidebar code can be found in /includes/helper-menu.html. The JavaScript that triggers the menu dropdown can be
found in /includes/js.html. We use the modal-id set in the post markdown to link to the hash of that post within its page
container.

## Adding posts

1) Add a new Markdown file to the appropriate category in the posts folder<br>
2) Jekyll enforces post dates so we just spoof the date in the order we want

## Adding new sections

To add a new section:

1) Add a section to the _config.yml where you want it to appear in the documentation menu tree<br>
2) Add a page folder, using the named ID you specified in the YAML<br>
3) Add an index.html in the folder and add the Markdown (use another page for an example)<br>
4) Add the posts directory, using the same name used for the page folder<br>
5) Add your post (see above)