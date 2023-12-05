# Gutenberg Blocks Cheat Sheet
 
 Markup for Gutenberg is written in HTML comments with added JSON attributes or features. The cheatsheet is inspired by [ Carolina Nymark's tutorials ](https://fullsiteediting.com/courses/full-site-editing-for-theme-developers/).

 ## File Tree

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

(and yes after years and years I still love the Bash tree command)

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

## A living document

This is a living document. If you have suggestions for more block samples, please let me know.