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

## Spacing

**settings.spacing**

~~~~
{
	"version": 2,
	"settings": {
		"spacing": {
			"blockGap": null,
			"customSpacingSize": true,
			"margin": false,
			"padding": false,
			"spacingScale": {
				"operator": "*",
				"increment": 1.5,
				"steps": 7,
				"mediumStep": 1.5,
				"unit": "rem"
			},
			"spacingSizes": [],
			"units": [ "px", "em", "rem", "vh", "vw", "%" ]
		}
	}
}
~~~~

## Typography

[Typography Article](https://developer.wordpress.org/themes/global-settings-and-styles/settings/typography/)

### Settings

~~~~
{
	"version": 2,
	"settings": {
		"typography": {
			"customFontSize": true,
			"dropCap": true,
			"fontStyle": true,
			"fontWeight": true,
			"letterSpacing": true,
			"lineHeight": false,
			"textColumns": false,
			"textDecoration": true,
			"textTransform": true,
			"writingMode": false
		}
	}
}
~~~~

### Font Families

How to add ordinary font families.

~~~~
{
	"$schema": "https://schemas.wp.org/trunk/theme.json",
	"version": 2,
	"settings": {
		"typography": {
			"fontFamilies": [
				{
					"name": "Primary",
					"slug": "primary",
					"fontFamily": "Charter, 'Bitstream Charter', 'Sitka Text', Cambria, serif"
				},
				{
					"name": "Secondary",
					"slug": "secondary",
					"fontFamily": "system-ui, sans-serif"
				}
			]
		}
	}
}
~~~~

These settings can be used in CSS as e.g.

~~~~
	var( --wp--preset--font-family--primary )
~~~~

### Web Fonts

Or how to enable fonts from files. Since these settings can be somewhat complex [read this article](https://developer.wordpress.org/themes/global-settings-and-styles/settings/typography/#registering-web-fonts-font-faces)

Below two fonts are defined:

~~~~
{
	"$schema": "https://schemas.wp.org/trunk/theme.json",
	"version": 2,
	"settings": {
		"typography": {
			"fontFamilies": [
				{
					"name": "Primary",
					"slug": "primary",
					"fontFamily": "Charter, 'Bitstream Charter', 'Sitka Text', Cambria, serif"
				},
				{
					"name": "Secondary",
					"slug": "secondary",
					"fontFamily": "'Open Sans', sans-serif",
					"fontFace": [
						{
							"fontFamily": "Open Sans",
							"fontWeight": "300 800",
							"fontStyle": "normal",
							"fontStretch": "normal",
							"src": [ "file:./assets/fonts/open-sans.woff2" ]
						},
						{
							"fontFamily": "Open Sans",
							"fontWeight": "300 800",
							"fontStyle": "italic",
							"fontStretch": "normal",
							"src": [ "file:./assets/fonts/open-sans-italic.woff2" ]
						}
					]
				}
			]
		}
	}
}
~~~~

### Use the fonts in the CSS

~~~~
body {
	--wp--preset--font-family--primary: Charter, 'Bitstream Charter', 'Sitka Text', Cambria, serif;
	--wp--preset--font-family--secondary: 'Open Sans', sans-serif;
}
~~~~

### Font Sizes

~~~~
{
	"version": 2,
	"settings": {
		"typography": {
			"fluid": false,
			"fontSizes": [
				{
					"name": "Small",
					"slug": "small",
					"size": "13px"
				},
				{
					"name": "Medium",
					"slug": "medium",
					"size": "20px"
				},
				{
					"name": "Large",
					"slug": "large",
					"size": "36px"
				},
				{
					"name": "Extra Large",
					"slug": "x-large",
					"size": "42px"
				}
			]
		}
	}
}
~~~~

## Root Padding

Is the padding around the `<body>` element. In the case below there will be no spacing on the top and bottom, but 2rem whitespace to right and left. Use these settings to set the general whitespace around your theme.

~~~~
{
	"version": 2,	
	"styles": {
		"spacing": {
			"padding": {
				"top": "0",
				"bottom": "0",
				"left": "2rem",
				"right": "2rem"
			}
		}
	}
}
~~~~

According to the article the JSON will output this CSS:

~~~~
body {
	padding-top: 0;
	padding-right: 2rem;
	padding-bottom: 0;
	padding-left: 2rem;
}
~~~~

**Note**: "But—and this is where things can look odd to seasoned designers—when settings.useRootPaddingAwareAlignments is enabled, the “root” padding is no longer applied to the root element. It is applied to container blocks like Group." [Quote](https://developer.wordpress.org/themes/global-settings-and-styles/settings/use-root-padding-aware-alignments/)

~~~~
{
	"version": 2,
	"settings": {
		"useRootPaddingAwareAlignments": true
	},	
	"styles": {
		"spacing": {
			"padding": {
				"top": "0",
				"bottom": "0",
				"left": "2rem",
				"right": "2rem"
			}
		}
	}
}
~~~~

## Blocks

Since we design everything in blocks, it is important to know how the blocks can be styled by *theme.json*.

All blocks can be styled along these lines:

~~~~
{
	"version": 2,
	"settings": {
		"blocks": {
			"core/button": {
				"border": {
					"radius": true
				}
			},
			"core/pullquote": {
				"border": {
					"color": true,
					"radius": true,
					"style": true,
					"width": true
				}
			}
		}
	}
}
~~~~

## Styling *Elements* and *Blocks*

**Elements** are *HTML elements* e.g. a tag like `<h1>`. Under elements you can style any alement. 

**Blocks** are the Gutenberg block styles, e.g. the behaviors of buttons and similar.

~~~~
{
	"version": 2,
	"styles": {
		"color": {
			"text": "#000000",
			"background": "#ffffff"
		},
		"elements": {
			"button": {
				"color": {
					"text": "#ffffff",
					"background": "#000000"
				}
			}
		},
		"blocks": {
			"core/code": {
				"color": {
					"text": "#ffffff",
					"background": "#000000"
				}
			}
		}
	}
}
~~~~

### Default Background and Text Color

In ordinary CSS the code below is similar to the styling of the `body` element. So this code will set the text and background color:

~~~~
{
	"version": 2,
	"styles": {
		"color": {
			"text": "#000000",
			"background": "#f5f1ea"
		}
	}
}
~~~~

**Tip:** Use the variables from your palette.

### Supported Elements

Not all HTML are supported here, but you can style these:

* button: Applied to `<button>` elements and button-like links, such as that used for the Button block.
* caption: Applied to media captions, which are wrapped in a `<figcaption>` element.
* cite: Applied to the `<cite>` element when used for citations, such as 
* heading: Applied to all heading elements from `<h1>` through `<h6>`, but these can be overridden for individual headings.
* h1 - h6: Each of the `<h1>` through `<h6>` elements can be individually styled.
* link: Applied to the `<a>` tag, which is used to create links

In the future we can hope that all elements will be supported. As of now only the elements above will work.

Here is a code sample. Note the pseudo classes (:hover):

~~~~
{
	"version": 2,
	"styles": {
		"elements": {
			"button": {
				"color": {
					"text": "#ffffff",
					"background": "#aa3f33"
				},
				":hover": {
					"color": {
						"background": "#822f27"
					}
				}
			}
		}
	}
}
~~~~

666 

## Style Variations

[Read about this here](https://developer.wordpress.org/themes/global-settings-and-styles/styles/applying-styles/#styling-block-style-variations-block-styles).

~~~~
{
	"version": 2,
	"styles": {
		"blocks": {
			"core/button": {
				"variations": {
					"outline": {
						"border": {
							"color": "currentColor",
							"style": "solid",
							"width": "2px"
						}
					}
				}
			}
		}
	}
}
~~~~

Only these elements support the variations option:

* core/button: outline, fill
* core/image: rounded
* core/quote: plain
* core/site-logo: rounded
* core/separator: wide, dots
* core/social-links: logos-only, pill-shape
* core/table: stripes
* core/tag-cloud: outline

### Block Typography

~~~~
{
	"version": 2,
	"styles": {
		"blocks": {
			"core/paragraph": {
				"typography": {
					"fontFamily": "Georgia, serif",
					"fontSize": "1.25rem",
					"fontStyle": "normal",
					"fontWeight": "500",
					"letterSpacing": "0",
					"lineHeight": "1.6",
					"textDecoration": "none"
				}
			}
		}
	}
}
~~~~

### Block CSS

You can style the block via CSS rules:

[Read about it here](https://developer.wordpress.org/themes/global-settings-and-styles/styles/styles-reference/#css)

~~~~
{
	"version": 2,
	"styles": {
		"blocks": {
			"core/gallery": {
				"css": "--wp--style--gallery-gap-default: 1rem;"
			}
		}
	}
}
~~~~

## Template Parts

Can be registered in theme.json, the sample will register *./parts/header.html* and *./parts/footer.html*:

~~~~
{
	"version": 2,
	"templateParts": [
		{
			"area": "header",
			"name": "header",
			"title": "Header"
		},
		{
			"area": "footer",
			"name": "footer",
			"title": "Footer"
		}
	]
}
~~~~

This should more or less cover the most important settings in theme.json files - or styles.

All code samples above have been copied from [https://developer.wordpress.org/themes/global-settings-and-styles/](https://developer.wordpress.org/themes/global-settings-and-styles/)