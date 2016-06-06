###FEWD Review Notes

---

####CSS Selectors
There are three basic ways to select html elements:

* by tag name
* by class name
* by id

Tag Name example:

	p {
		...
	}
	
...would grab every `<p>` tag on the page.

Class name example:

	.column {
		...
	}
	
...would grab every element with a class attribute of "column", so `<div class="column">`, `<h1 class="column">`, etc.

id example:

	#logo {
		...
	}
	
Grabs the one element on the page (and there should only be one) with the id attribute of "logo" (e.g., `<img src="image.jpg" id="logo">`)

Remember that we use **class** to target a group of elements and **id** to target a single element.

In addition to the three basic CSS selectors, there are other selectors we can use to make more targeted selections. Three two most common follow these patterns:

* tagname tagname (e.g. `div h1`)
* .classname tagname (e.g. `.menu li`)

tagname tagname example:

	div h1 {
		...
	}

Grabs all `<h1>` tags inside of `<div>` tags

	<div>
		<h1>hi</h1>
	</div>

.classname tagname example:

	.blog-post p {
		...
	}
	
Grabs all `<p>` elements inside or any element with a class of `.blog-post`:

	<article class="blog-post">
		<p>hello world</p>
		<p>hello world</p>
	</article>

---

####The Box Model
The CSS box model states that all HTML elements are boxes that consist of for parts--contents, padding, border, and margin.

![box model](../../../img/unit_1/box-model.png)

We can manipulate the parts of the box model with CSS:


	div {
		border: 1px solid #CCC;
		padding-bottom: 10px;
		margin-top: 5px;
	}

Remember that we can use **shorthand properties** to avoid having to type out `margin-top` and `margin-bottom`, etc. all the time:

This applies 10px of padding to all sides of  a `<div>`:

	div {
		padding: 10px
	}

This applies a 10px margin to the top and bottom of an `<h1>` and a 20px margin to the left and right of it:

	h1 {
		margin: 10px 20px;
	}
	
Remember too that we can use box margin properties to **horizontally center** elements:

	div {
		margin: 0 auto;
	}
	
Remember that there are different implementations of the box model in CSS--content-box, padding-box, and border-box. The most intuitive is border-box, which defines an elements height and width as its content + padding + border. To make your page use the border-box implementation, paste the following snippet into the start of your CSS file:	

	*,
	*:before,
	*:after {
		-webkit-box-sizing: border-box;
		   -moz-box-sizing: border-box;
			    box-sizing: border-box;
	}


---

####Block vs Inline Elements
HTML elements gernerally fall into one of two categories--block or inline. Block elements expand to fill all available horizontal space in the browser window. Inline elements take up only as much horizontal space as their contents need.

Block elements always stack on top of each other. Inline elements on the other hand can go side by side if space allows.

Inline elements are limited in that they can't take certain css properties like `height` and `width`. Block elements are limited in that they can't be positioned side by side. To overcome these limitations, CSS has the **inline-block** element, which behaves like both a block and an inline element. Inline-block elements can be positioned side by side, but they can also be assigned a height and a width.

To change an elements value from block/inline, use the `display` property:

	div {
		display: inline-block;
	}
	
	span {
		display: block;
	}
	
---

####CSS Resets
Web-browsers have stylesheets built into them. These stylesheets apply default styles to HTML elements. They will for example make all `<h1>` elements have a font-size of 36px.

These default styles often disrupt our own layouts, and they vary from browser to browser, making it difficult to achieve a consistent look on a page. To overcome this, use a CSS reset. This is just a set of pre-defined CSS rules wipes out common default styles, clearing the way for our own CSS rules.

The most commonly used CSS reset is this one, written by Eric Meyer:

	
	html, body, div, span, applet, object, iframe,
	h1, h2, h3, h4, h5, h6, p, blockquote, pre,
	a, abbr, acronym, address, big, cite, code,
	del, dfn, em, img, ins, kbd, q, s, samp,
	small, strike, strong, sub, sup, tt, var,
	b, u, i, center,
	dl, dt, dd, ol, ul, li,
	fieldset, form, label, legend,
	table, caption, tbody, tfoot, thead, tr, th, td,
	article, aside, canvas, details, embed, 
	figure, figcaption, footer, header, hgroup, 
	menu, nav, output, ruby, section, summary,
	time, mark, audio, video {
		margin: 0;
		padding: 0;
		border: 0;
		font-size: 100%;
		font: inherit;
		vertical-align: baseline;
	}
	
	article, aside, details, figcaption, figure, 
	footer, header, hgroup, menu, nav, section {
		display: block;
	}
	body {
		line-height: 1;
	}
	ol, ul {
		list-style: none;
	}
	blockquote, q {
		quotes: none;
	}
	blockquote:before, blockquote:after,
	q:before, q:after {
		content: '';
		content: none;
	}
	table {
		border-collapse: collapse;
		border-spacing: 0;
	}

To use it, just copy and past it at the beginning of your own CSS file.

---

####Resources
* [The Box Model](http://learn.shayhowe.com/html-css/opening-the-box-model/) - a good overview of the box model by developer Shay Howe. 
* [Block, Inline, and the Display Property](http://www.w3schools.com/css/css_display_visibility.asp) - an overview of display property from the W3C. Several interactive examples
* [CSS Diner](http://flukeout.github.io/) - a fun game that will let you practice beginner to advanced CSS selections
* [JavaScript Basics](http://jsforcats.com/) - for those who want a taste of what's coming up, here is a very short intro to JavaScript. This tutorial requires no special setup beyond having Google Chrome on your computer 
