# Theme JSON

The *theme.json* file is the main styling document. This file can be complex, and in order to use it you must at least have some knowledge about CSS and JSON. Here you can define the options for fonts, colors, gradients, layout and more options for the end user that will edit content in the Dashboard. The theme.json file must be placed in the root of the theme directory. The source for the code samples in this file is [https://developer.wordpress.org/themes/global-settings-and-styles/](https://developer.wordpress.org/themes/global-settings-and-styles/).

However, you can create style variations. I could just be a copy of your theme.json, but with alternative fonts, colors, layout etc. Place these files in the styles directory. Here arer a few alternative styles from the *Twenty Twenty Four* theme:

~~~~
├── ember.json
├── fossil.json
├── ice.json
├── maelstrom.json
├── mint.json
├── onyx.json
├── petj_rust.json
└── rust.json
~~~~

All these files are simply variations of the basic *theme.json*. Creating your own variation may be as simples as copy-pasting a style that you like and add whatever colors or fonts you want. The file *petj_rust.json* is such a file.

## Basic structure

Here is the basic theme.json structure.

~~~~
{
	"version": 2,
    "$schema": "https://schemas.wp.org/trunk/theme.json",
	"settings": {
		"appearanceTools": false,
		"border": {},
		"color": {},
		"custom": {},
		"dimensions": {},
		"layout": {},
		"position": {},
		"shadow": {},
		"spacing": {},
		"typography": {},
		"useRootPaddingAwareAlignments": false,
		"blocks": {}
	}
}
~~~~

## Appearance Tools

The catch all is:

~~~~
{
	"version": 2,
	"settings": {
		"appearanceTools": true
	}
}
~~~~

However, you may want to enable or disable features by booleans:

~~~~
{
	"version": 2,
	"settings": {
		"border": {
			"color": true,
			"radius": true,
			"style": true,
			"width": true
		},
		"color": {
			"link": true
		},
		"dimensions": {
			"minHeight": true
		},
		"position": {
			"sticky": true
		},
		"spacing": {
			"blockGap": true,
			"margin": true,
			"padding": true
		},
		"typography": {
			"lineHeight": true
		}
	}
}
~~~~

## Border

**settings.border**

Read: [https://developer.wordpress.org/themes/global-settings-and-styles/settings/border/](https://developer.wordpress.org/themes/global-settings-and-styles/settings/border/)

~~~~
{
	"version": 2,
	"settings": {
		"border": {
			"color": false,
			"radius": false,
			"style": false,
			"width": false
		}
	}
}
~~~~

## Color

**settings.color**

Again the enable/disable of color options is defined by booleans.

~~~~
{
	"version": 2,
	"settings": {
		"color": {
			"background": true,
			"custom": true,
			"customDuotone": true,
			"customGradient": true,
			"defaultDuotone": true,
			"defaultGradients": true,
			"defaultPalette": true,
			"duotone": [],
			"gradients": [],
			"link": true,
			"palette": [],
			"text": true
		}
	}
}
~~~~

## Define the global Color Palette for the theme

**settings.color**

The colors are defined by:

* Color: a CSS hex code for the color
* Name: a human readable name for the color
* Slug: a slug that will create a CSS-variable you can use when styling elements

### Defining a Palette

~~~~
{
	"version": 2,
	"settings": {
		"color": {
			"palette": [
				{
					"color": "#ffffff",
					"name": "Base",
					"slug": "base"
				},
				{
					"color": "#000000",
					"name": "Contrast",
					"slug": "contrast"
				},
				{
					"color": "#89CFF0",
					"name": "Primary",
					"slug": "primary"
				}
			]
		}
	}
}
~~~~

### The Slug will Create a CSS variable

The slug will create a CSS variable, like:

**--wp--preset--color--SLUG**

When styling HTML elements, you can invoke the gradient, like:

~~~~
var( --wp--preset--color--contrast )
~~~~

## Gradients

**settings.color.gradients**

~~~~
{
	"version": 2,
	"settings": {
		"color": {
			"gradients": [
				{
					"gradient": "linear-gradient(to right, #10b981, #64a30d)",
					"name": "Emerald",
					"slug": "emerald"
				},
				{
					"gradient": "linear-gradient(-225deg,#231557,#44107a 29%,#ff1361 67%,#fff800)",
					"name": "Fabled Sunset",
					"slug": "fabled-sunset"
				}
			]
		}
	}
}
~~~~

## Duotones

**settings.color.duotones**

Duotones will transform images to duotone graphics. This effect is cool, IMHO.

~~~~
{
	"$schema": "https://schemas.wp.org/trunk/theme.json",
	"version": 2,
	"settings": {
		"color": {
			"duotone": [
				{
					"colors": [
						"#450a0a",
						"#fef2f2"
					],
					"name": "Red",
					"slug": "red"
				},
				{
					"colors": [
						"#172554",
						"#eff6ff"
					],
					"name": "Blue",
					"slug": "blue"
				}
			]
		}
	}
}
~~~~

## Layout

**settings.layout**

The width of your content. 

~~~~
{
	"version": 2,
	"settings": {
		"layout": {
			"contentSize": "40rem",
			"wideSize": "64rem"
		}
	}
}
~~~~

## Enable Lightbox

The default is *false* - here is how to enable Lightbox editing:

~~~~
{
	"version": 2,
	"settings": {
		"blocks": {
			"core/image": {
				"lightbox": {
					"allowEditing": true
				}
			}
		}
	}
}
~~~~

This will enable Lightbox:

~~~~
{
	"version": 2,
	"settings": {
		"blocks": {
			"core/image": {
				"lightbox": {
					"enabled": true
				}
			}
		}
	}
}
~~~~

## Sticky positioning

Practical for e.g. menus and similar navigation elements.

~~~~
{
	"version": 2,
	"settings": {
		"position": {
			"sticky": true
		}
	}
}
~~~~

How to use it, see this image [https://developer.wordpress.org/files/2023/10/position-sticky-header.jpg](https://developer.wordpress.org/files/2023/10/position-sticky-header.jpg)

# Here:

Just where I am reading the docs ... 

[https://developer.wordpress.org/themes/global-settings-and-styles/settings/spacing/](https://developer.wordpress.org/themes/global-settings-and-styles/settings/spacing/)