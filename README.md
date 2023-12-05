# Gutenberg Blocks Cheat Sheet
 
 Markup for Gutenberg is written in HTML comments with added JSON attributes or features. The cheatsheet is inspired by [ Carolina Nymark's tutorials ](https://fullsiteediting.com/courses/full-site-editing-for-theme-developers/). But I have tried to simplify the content in a way that's more easy to remember - at least for me.

 Since everything is made with HTML, CSS and JavaScript you will be able to create any kind of content or design in a block based theme. The Gutenberg specific blocks are comments with a JSON object.

 Most humans will not be able to remember the names of the blocks. But you can create your design in Gutenberg. When you like what you see change the editor to code view. Now you can save your design in one of the template files. E.g. if you want the design to be your front page save the Gutenberg Markup in *front-page.html*.

 ## Why Create a Theme from Scratch

 The polished themes are nice. But, you learn a *lot* about Gutenberg when you create your own theme. Then you are not limited by the themes any more. You'll be able to make your own stuff. Try to create a theme - and you will be able to add new features to any block based theme. 

 Often the *modus operandi* is: copy a file like ./templates/single.html to ./templates/single-SLUG.html - and then add the features you need. Perhaps you want to add your favorite gallery that you made in Vanilla JavaScript. By your own ingenium device similar samples.

 ## Sample Theme

 Here is my sample theme. It was made when I followed Nymark's tutorial:

 * [Theme on Github](https://github.com/asathoor/myBlock)

 ## The File Tree

 Will look something along these lines. You can add a styles directory for alternative theme.json files. Templates and template parts are HTML files. The styling is primarily made via theme.json - but you can add CSS rules to style.css.

~~~~
 ── functions.php
├── parts
│   ├── footer.html
│   └── header.html
├── style.css
├── templates
│   ├── archive.html
│   ├── front-page.html
│   ├── index.html
│   ├── page.html
│   ├── search.html
│   ├── single-map.html
│   ├── single-nocomments.html
│   └── single.html
└── theme.json
~~~~

(And yes, after years and years I still love the *Bash* tree command)

 ## Include Header

~~~~
    <!-- wp:template-part {"slug":"header","tagName":"header","className":"site-header"} /-->
~~~~

## Include Footer
~~~~
<!-- wp:template-part {"slug":"footer","tagName":"footer","className":"site-footer"} /-->
~~~~

## Include any Template or Template Part

The files must be named after the WordPress file hierarchy. However, in block based themes the files are .html and not .php (at least most files are, but you can create PHP-files).

A file is named something like:

* ./templates/page-withMap.html

You can include a similar file like this:

~~~~
<!-- wp:template-part {"slug":"page-withMap","tagName":"footer","className":"site-footer"} /-->
~~~~

Note that the **slug** is the first part of the filename. You just omit the .html part.

## Semantic Markup: main

~~~~
<!-- wp:group {"tagName":"main","layout":{"type":"constrained"}} -->
    <main class="wp-block-group">

        ... you can add more content here ...

    </main>
<!-- /wp:group -->
~~~~

## Custom HTML

You can add custom HTML, CSS and JavaScript anywhere in the template. Use a Custom HTML block for the purpose. Below I have added an iframe with an OpenStreetMaå:

~~~~
		<!-- wp:html -->
			<div style="height:40px" aria-hidden="true" class="wp-block-spacer"></div>
			<div>
				<iframe width="425" height="350" src="https://www.openstreetmap.org/export/embed.html?bbox=9.71672058105469%2C56.01949427177337%2C10.533828735351562%2C56.269667554101495&amp;layer=mapnik" style="border: 1px solid black"></iframe><br/><small><a href="https://www.openstreetmap.org/#map=11/56.1448/10.1253">View Larger Map</a></small>
			</div>
			<div style="height:40px" aria-hidden="true" class="wp-block-spacer"></div>
		<!-- /wp:html -->
~~~~

If you want to add galleries from JsFiddle or Codepen just add the code in this order:

* CSS
* HTML
* JavaScript

## Posts and Pages

~~~~
<!-- wp:post-featured-image /-->
<!-- wp:post-title /-->
<!-- wp:post-author {"showAvatar":true} /-->
<!-- wp:post-date /-->
<!-- wp:post-terms {"term":"category"} /-->
~~~~

## Whitespace (aka Spacer)

~~~~
<!-- wp:spacer {"height":"40px"} -->
    <div style="height:40px" aria-hidden="true" class="wp-block-spacer"></div>
<!-- /wp:spacer -->
~~~~

## Post Tag
~~~~
<!-- wp:post-terms {"term":"post_tag"} /-->
~~~~

## Post Content

The block below will add the actual content from a page or post:

~~~~
<!-- wp:post-content /-->
<!-- wp:spacer {"height":"40px"} -->
    <div style="height:40px" aria-hidden="true" class="wp-block-spacer"></div>
<!-- /wp:spacer -->
~~~~

The post content block is not as advanced as the *post query*. 

## Post Query

In a post query we ask the database for certain informations. We can filter these informations by taxonomies, like *categories* or *tags*. Here is a query:

~~~~
<!-- wp:query {"queryId":9,"query":{"perPage":7,"pages":0,"offset":0,"postType":"post","order":"desc","orderBy":"date","author":"","search":"","exclude":[],"sticky":"exclude","inherit":true}} -->
<div class="wp-block-query"><!-- wp:post-template {"layout":{"type":"grid","columnCount":3}} -->
<!-- wp:group {"style":{"spacing":{"padding":{"top":"30px","right":"30px","bottom":"30px","left":"30px"}}},"layout":{"inherit":false}} -->
<div class="wp-block-group" style="padding-top:30px;padding-right:30px;padding-bottom:30px;padding-left:30px"><!-- wp:post-title {"isLink":true} /-->

<!-- wp:post-content /-->
<!-- wp:post-date /--></div>
<!-- /wp:group -->
<!-- /wp:post-template --></div>
<!-- /wp:query -->
~~~~

### Filters

You can filter the content by these parameters:

~~~~
{"perPage":7, // = number of posts shown
"pages":0, // = pages
"offset":0, // if you have more than one loop change the offset
"postType":"post", // or page
"order":"desc", // or asc
"orderBy":"date", // try: author, id, etc.
"author":"", // filter a certain author
"search":"", // e.g. a category
"exclude":[], // what you don't want to see
"sticky":"exclude", // or include
"inherit":true} // or false
~~~~

Since you can have more than one queries on a page the offset should match the pages of the previous query. In the case above we could create a new query, like:

~~~~
{"perPage":7, // = number of posts shown
"pages":0, // = pages
**"offset":7**, // if you have more than one loop change the offset
"postType":"post", // or page
"order":"desc", // or asc
"orderBy":"date", // try: author, id, etc.
"author":"", // filter a certain author
"search":"", // e.g. a category
"exclude":[], // what you don't want to see
"sticky":"exclude", // or include
"inherit":true} // or false
~~~~

## Post Excerpt

The excerpt is a short teaser for a post or page. 

~~~~
<!-- wp:post-excerpt /-->
~~~~

## A Template Sample

Here is a template sample, this samle is inspired by Carolina Nymark's tutorial op.cit.:

~~~~
<!-- wp:template-part {"slug":"header","tagName":"header","className":"site-header"} /-->

<!-- wp:group {"tagName":"main","layout":{"type":"constrained"}} -->
	<main class="wp-block-group">
		<!-- wp:query -->
			<div class="wp-block-query">
				<!-- wp:post-template -->
				<!-- wp:post-featured-image /-->
				<!-- wp:post-title {"isLink":true} /-->
				<!-- wp:post-author {"showAvatar":false} /-->
				<!-- wp:post-date /-->
				<!-- wp:post-terms {"term":"category"} /-->
				<!-- wp:post-excerpt /-->
				<!-- /wp:post-template -->
				<!-- wp:query-pagination -->
			<div class="wp-block-query-pagination">
				<!-- wp:query-pagination-previous /-->
				<!-- wp:query-pagination-next /-->
			</div>
		<!-- /wp:query-pagination -->
			</div>
		<!-- /wp:query -->
	</main>
<!-- /wp:group -->

<!-- wp:template-part {"slug":"footer","tagName":"footer","className":"site-footer"} /-->
~~~~

## theme.json - options and consistency

The *theme.json* file the new way for styling WP. Here we define the fonts, colors and style options of the solution. The *theme.json* file will enable options in the Gutenberg editor - so that you can choose colors, gradients, fonts and so on. It is also possible to lock options, so that the ordinary user is forced to use the theme colors. In this way we can ensure design consistency.

Below is my link to the *theme.json*:

* [theme.json sample](https://github.com/asathoor/myBlock/blob/main/theme.json)


## Theme Generators

Since the theme code is based on JavaScript automation is possible. There are several theme generators on the web.

* [Nymark: Theme Generator](https://fullsiteediting.com/block-theme-generator/)

## A living document

This is a living document. If you have suggestions for more block samples, please let me know.