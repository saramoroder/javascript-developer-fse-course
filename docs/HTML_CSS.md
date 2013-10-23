#HTML and CSS

HTML for semantics

CSS for styles

JS for interaction

HTTP (GET,POST,PUT,DELETE)

PHP language side programming language for the web

- apache2 server web
- libapache2-mod-php5
- php5 interprete PHP
- php5-mysql
- mysql-server
- phpmyadmin o mysql-client

##HTML

sgml, basic language

tree structure

tags for semantics (SEO)

doctype defines the document type 

	<!DOCTYPE

contains the document type definisce (dtd)

strict mode

transitional mode

frameset mode

important for bots,seo

	<nametag attribute="value">
		content
	</nametag>

structure and content

void tags, like img are closed with / before >

tags inside head are interpreted, inside body are displayed


meta are closed with / before > because they are void tags

	<meta name="author" content="Christian Fei" />
	<meta http-equiv="content-type" content="text/html; charset=UTF-8"/>
	<meta http-equiv="content-language" content="it"/>
	<meta name="description" content="descrrizione pertinente della pagina"/>
	<meta name="copyright" content="Christian Fei 2013"/>
	<meta http-equiv="refresh" content="5; http://www.google.com"/>
	<meta name="robots" content="index,follow"/>
	<meta charset="utf-8"/>

in html5


html entities

represents the html character literally, start with &

	&egrave;
	
&egrave;

	&lt; &gt;

&lt; &gt;


There are different types of tags

-block have dimensions, follow the box-model, have a break line afterwards
-inline 

####block elements
p, h1-h6, blockquote,address,pre,div

div: general block element, used to define the structure of the page

####inline elements
get displayed on the same line

aim: identify differnet pieces of text with different meanings

e.g.:acronym,abbr,cite,code,q,dfn,q,span

span:the most generic inline element

####Attributes
generic attributes:title,style,id,class

---------

#####three steps

1. structure
2. content
3. presentation


##CSS
	selector {
		property:value;
	}

###units
- px
- %
- em,rem
- cm
- pt

Cascading stylesheets..
only the last definition of the cascade will take effect on the element

properties are overridden if they are more specific

#08/10/2013

##stylesheets

Three methods

- external
- embedded
- inline

####embedded

	<style type="text/css">
		p{
			font-weight: bold;
		}
	</style>

####inline
	
	<p style="font-weight:bold">
		text
	</p>

this is more specific

[read this](http://css-tricks.com/specifics-on-css-specificity/)

####external

	<link rel="stylesheet" href="http://google.com/style.css" type="text/css" />

###Order

1. external
2. embedded
3. inline

###Print stylesheets

	<link rel="stylesheet" type="text/css" media="print" href="print.css">

###rulez

	text-align:left|right|center|justify;

is applied to block elements, result:
inline elements inside are aligned accordingly.

*shorthand property*

	background: #ccc url('img/m.jpg') no-repeat center right fixed;

background-size is CSS3, don't use it in the shorthand because old browsers could interpret the whole property as invalid

###pseudo-classes

	a:link{}
	a:visited{}
	a:hover{}
	a:active{}
	/*in this ordero ordine. LoVe HAte*/

	a:first-letter
	div:first-child


##images

####non-vector
- jpg
- gif
- png (high quality, handles transparency)

####raster type images

can be optimized pixel per pixel (jpg,png)
IE6 +/- has problemes with PNG

attribute width and height are deprecatated

####vertical align

can be applied to inline elements
top,bottom,middle,super,sub,text-top,text-bottom

####line-height

useful to create button with centred text(see padding too)

###box model

![box-model](http://screencloud.net/img/screenshots/74e10063dfbec7d00642079c63087f82.png)

block elements follow this spec

**width***,*height***,*border**

**width** is default 100% relatively to its parent

**padding** is the distance between content and border

**border**

**outline** acts like a second border

**margin** creates a space between the element and its container

**width** and **height** define the dimensions of the content

#Positioning

	position:static|relative|absolute|fixed; /*static is default*/

Can be applied to block elements.

when a parent element has a defined height, its child elements are displayed in a layer above and overflow the layer afterwards

remains in the document flow


##relative
the element is relative to its parent container.

the element is displayed on an own layer but acts like a static element (the dimensions and position are the same as an static element)

new CSS properties are now available (top left, etc)

Use case: banners


##absolute

we brake the element away from the normal document flow (static)

the base structure don't know that the element exists because it's on an own layer

doesn't get displayed until there isn't another parent element with a position different to static


##fixed

Position elements relative to the browser window. When the window scrolls, the element stays at the same position.

###z-index

defines the layer level of an element

###float

cancels out the block element properties and places elements in a specific position (left,right)

Are taken away from the regular document flow!

The order in which elements are floated is important!

Beware of collapsing parents!

![float](http://screencloud.net/img/screenshots/39fbc89d55d994e1e2416545fca79f35.png)

fills out also the vertical gaps

####clear

The clear property cancels out the flow of floated elements. (right,left,both)

##display

with display we can inherit properties of other element tipes (block, inline,inline-block,none,table,etc.)

####block

e.g.: `a {display:block;}` enables links (inline elements) to have dimensions and follow the box-model (padding, height, margin,etc)

####inline-block

With `inline-block`  we can inherit the properties of inline elements with dimensions (like images, svg, etc)

####inline

The `inline` property is rendered depending on its content (wrap-content), in other words the elements has the dimensions of the text inside of it. 

####none

take the element out of the structure, the element doesn't affect elements nearby

##lists
	
	list-style-type: circle|square|none|etc.
	list-style-position:inside|outside;

`ul` e `ol` (unordered e ordered list, same properties, one is dotted the other is numbered

`li` (list items)

`dl` description list

`dt` data title

`dd` data definition

**outside**
![outside](http://screencloud.net/img/screenshots/24c26d710a6799596a4ab3ef5e921aaa.png)

**inside**
![inside](http://screencloud.net/img/screenshots/6c14a321cf02c65faa195575adc77461.png)

###nested lists

####css

	li ul{
		display: none;
	}
	li:hover > ul{
		display:block;
	}

####html

	<ul>
		<li>menu1</li>
		<li>menu2</li>
		<li>menu3
			<ul>
				<li>submenu3.1</li>
				<li>submenu3.2
					<ul>
						<li>subsubmenu3.2.1</li>
						<li>subsubmenu3.2.2</li>
						<li>subsubmenu3.2.3
							<ul>
								<li>subsubsubmenu3.2.3.1</li>
								<li>subsubsubmenu3.2.3.2</li>
							</ul>
						</li>
					</ul>
				</li>
			</ul>
		</li>
	</ul>

##visibility

visually hides the element but retains the static dimension it has in the document flow

##tables

	<table>
		<tr> //table row
			<th> //table heading
			<td> //table cell

only border is supported in [HTML5](http://www.w3schools.com/tags/tag_table.asp) other attributes are deprecated


	table,th,td{
		border:1px solid black;
	}

has the same effect as
	
	<table border="1">

####border-collapse
applied to table
	border-collapse: collapse|separate;

####border-spacing
applied to table

	border-spacing:10px 5px; //horizontal and vertical spacing

####empty-cells
	
	empty-cells: hide|show;

####colspan|rowspan

	<tr>
		<th>heading 1</th>
		<th>heading 2</th>
		<th>heading 3</th>
	</tr>
	<tr>
		<td colspan="2">cell2</td>
		<td>cell3</td>
	</tr>

give a title to a table with
	
	<caption>title</caption>

you can specify the position of the caption with
	
	caption-side: bottom|top;

Give finer grained structure to your table with
	
	<thead>
	<tbody>
	<tfoot>

**warning** normally the HTML interpreter automatically adds a tbody around the content of a table elements (good to know for DOM navigation)


#####example

	<table>
		<caption>my table</caption>
		<tr>
			<th>heading 1</th>
			<th>heading 2</th>
			<th>heading 3</th>
		</tr>
		<tr>
			<td colspan="2">cell1</td>
			<td>cell2</td>
		</tr>
		<tr>
			<td rowspan="2">cell1</td>
			<td>cell2</td>
			<td>cell3</td>
		</tr>
		<tr>
			<td colspan="2">cell2</td>
		</tr>
	</table>

equals this

![table layout](http://screencloud.net/img/screenshots/61f43fe8c884ea270dcbba092532dd5f.png)

####table-layout

Defines the layout of the table: auto (default), fixed

Works in conjunction with a specific width set to td and th.

	table{
		table-layout:fixed;
	}
	th,td{
		width:100px;
	}

Doesn't work with non-breakable words, like (fdsfdsfdsfsfadsfdasfdsafsdafds)

![table with fixed width and layout fixed](http://screencloud.net/img/screenshots/6edd2fa65bd9a8ebff8c474efc9f6af7.png)

####semantics in tables

abbr attribute on td's

summary attribute on table

####colgroup

colgroup is used to apply styles to entire columns of a table

	<colgroup>
		<col style="background-color:red"/>
		<col style="background-color:blue"/>
		<col style="background-color:yellow"/>
	</colgroup>

placed after caption and before thead,tbody

----

*hint*

to hide overflowing text with an ellipsis you need to do the following:

	td,th{
		max-width: 100px;
		overflow: hidden;
		text-overflow: ellipsis;
	}

####border-radius

pass horizontal and vertical radius.

Via shorthand or each corner:
	
	border-radius: 10px 5px;

	border-top-left-radius:50%;

	border-radius: 40px 30px 20px 10px / 40px 30px 20px 10px;

##form

Is the interface that connects a browser with a web server. A language capable to process the data sent from a form needs to be parsed on the server (PHP,Node,etc)

Every information I want to send to the server needs to be inside `<form>`

####attributes

	<form name="myform" id="myform" action="result.php" method="get">

	</form>

`name` identifies the form

`action` is the file/service that will handle my request (hopefully)

`method` is the method to transport the data, GET (sent through parameters in the url), POST (sent 'anonymously')

##input

attribute `type` defines the type of the input: text, password, submit, etc.

`name` attribute is used to identify data on the server side

The name attribute gets interesting when used with radio buttons

	<input type="radio" id="M" name="sex" value="M"> M
	<input type="radio" id="F" name="sex" value="F"> F


In this case the browser understands that only one option can be selected thanks to the same name attribute of both input[type="radio"]

**hint** : the value attribute is needed in this case because we need to identify further which radio button has been selected

####checkbox

	<input type="checkbox" name="dog" id="dog">dog

additional attribute : `checked`, reccommended syntax
	
	<input type="checkbox" name="dog" id="dog" checked="checked">dog

####select

	<select name="city" id="city">
		<option value="Bolzano">Bolzano</option>
		<option value="Merano">Merano</option>
	</select>

Where the value attribute of the option tags are the values sent through a HTTP request

To send multiple choiches (hold down ctrl to select more)
	
	<select name="city[]" id="">
		<option value="Bolzano">Bolzano</option>
		<option value="Merano">Merano</option>
	</select>

####reset

Resets the form to its default state

	<input type="reset" value="reset">

####button

	<input type="button">

####datalist

The `<datalist>` tag specifies a list of pre-defined options for an `<input>` element.

The `<datalist>` tag is used to provide an "autocomplete" feature on `<input>` elements. Users will see a drop-down list of pre-defined options as they input data.

Use the `<input>` element's list attribute to bind it together with a `<datalist>` element.

	<input list="browsers">

	<datalist id="browsers">
	  <option value="Internet Explorer">
	  <option value="Firefox">
	  <option value="Chrome">
	  <option value="Opera">
	  <option value="Safari">
	</datalist>
####new attributes and tags in HTML5 forms

**beware** partial support even in 'modern' browsers

	<input type="email">
	<input type="url">
	<input type="number" min="10" max="20">
	<input type="range" min="10" max="20"/>
	<input type="date">
	<input type="week">
	<input type="month">

attribute `required` on form children, `novalidate` on form for debug purpose

`pattern` for client side validation (browser support)

`placeholder` text

`autofocus="autofocus"`

Input elements have indexes and you can navigate through them with tabulator. You can specify an order with the attribute `tabindex`

`readonly` gets sent through forms

`disabled` doesn't

------

	<label for="link"></label>
	<input type="text" id="link" name="link">

for better usability

------

	<fieldset>
		<legend>title of the form</legend>
		<form action="">
			<input type="text">
		</form>
	</fieldset>

####new pseudo-classes

	input:valid,input:invalid{}

####pseudo-elementi

	:after, :before{}

##external resources

####object

`object` and `embed`

`object` has more support

	<object data="" type="">
		<embed src="" type="">
	</object>

It's an inline element

	<object data="adb.pdf" type="application/pdf">
		<embed src="abc.pdf" type="application/pdf"/>
	</object>

elements inside `object` are used as a fallback

	<object data="adb.pdf" type="application/pdf">
		alt <a href="abc.pdf">test</a>
	</object>

	<object data="adb.pdf" type="application/pdf">
		<embed src="abc.pdf" type="application/pdf"/>
	</object>

result are very different across browsers..

####iframe

	<iframe src="http://www.ethicalsoftware.it" frameborder="0"></iframe>

`sandbox` attribute allow to specify resource to load inside an iframe

void `sandbox` attribute set these four allowed attributes:

- allow-same-origin
- allow-top-navigation
- allow-forms
- allow-scripts

####video

attributes
	
	controls
	autoplay

for better fallback use this technique
	
	<video controls="controls" height="240" width="320">
		<source src="movie.mp4" type="video/mp4"/>
		<source src="movie.ogg" type="video/ogg"/>
		<object width="320" height="240">
			<embed src="movie.swf" width="320" height="240">
			</embed>
		</object>
	</video>

####audio

same as above

##SVG

	<svg height="200" width="200" xmlns="http://www.w3.org/2000/svg">

	</svg>

Every geometric form of the SVG goes inside this tag.

Not everything of an SVG can be styled via CSS, like rect for example

	<rect id="rectangle" width="50" height="50" fill="yellow" x="20" y="40"/>

	<circle cx="100" cy="100" r="50"/>

	<line x1="70" y1="40" x2="250" y2="100" stroke="black" stroke-width="2"/>

	<polygon points="50,10,200,50,100,50,50,150,150,200" fill="none" stroke="blue" stroke-width="2"/>
	
	<polyline points="300,150,250,75,150,80,50,175" stroke="black" stroke-width="2" fill="none"/>

####minigolf

	<svg height="200" width="300" xmlns="http://www.w3.org/2000/svg" style="background-color:white;">
		<polygon points="0,150,140,150,140,0,145,0,190,20,145,40,145,150,300,150,300,200,0,200,0,150" stroke-width="2" stroke="black"/>
	</svg>

![minigolf](http://screencloud.net/img/screenshots/2c3f3493b8d17103cd95723f8082e599.png)

####animating SVG

void elements need become enclosing tags

##HTML5 new structure elements

####section

The `<section>` tag defines sections in a document, such as chapters, headers, footers, or any other sections of the document.

####aside

The `<aside>` tag defines some content aside from the content it is placed in.

The aside content should be related to the surrounding content.

####article

The `<article>` tag specifies independent, self-contained content.

An article should make sense on its own and it should be possible to distribute it independently from the rest of the site.

Potential sources for the `<article>` element:

- Forum post
- Blog post
- News story
- Comment

####figure

Identifies a surrounding box around an image. In conjunction with figcaption bots can understand and index the site content better (SEO)

#####figcaption

Description of the image. Goes inside the figure element

	<figure>
		<img src="bb.jpg" alt="brooklyn bridge">
		<figcaption>brooklyn bridge</figcaption>
	</figure>

####mark

Highlights part of your text

####meter

	<meter min="0" max="100" value="75"></meter>
	<meter value="0.75"></meter>

Example usage : `disk usage`.

It's not meant for progress visualization: use `<progress>` instead.

**These elements are not production ready, are cool, but it's not safe to use them**

##new CSS3 properties

####box-shadow

Can be applied to containers (like inline-block,block,etc.)

	box-shadow: 50px 50px 10px 20px deepskyblue;

####background-origin

Decide from where to let the background-image start (regarding the box-model)

Three options
	
	backgroud-origin: content-box| padding-box|border-box;

##Colums

	-webkit-column-count: 3;
	-moz-column-count: 3;
	column-count: 3;

Creates a grid layout of the block element with 3 columns

####column-gap

You can define a gap between each column

	-webkit-column-gap: 41px;
	-moz-column-gap: 41px;
	column-gap: 41px;

####column-rule
	
Show a border between each column

	-webkit-column-rule: 1px solid black;
	-moz-column-rule: 1px solid black;
	column-rule: 1px solid black;

##Vendor prefixes

Every browser can specify their own libraries etc., so you have to adapt and use vendor prefixes.

[CSS3 vendor prefixes](http://www.w3schools.com/cssref/css3_browsersupport.asp)

##External fonts in CSS3

You can let the browser download a custom font for your website with CSS3

	@font-face{
		font-family: myfont; /*declare your custom font*/
		src: url('fonts/black_r.ttf'),
				url('fonts/black_r.eot') format('opentype');
	}

	body{
		font-family: myfont; /*use your custom font*/
	}

##media queries

`media` attribute in `<link>` to specify a stylesheet for a specific media type (screen,tv,projector,print,etc.)

OR

`@media` in CSS3

	@media screen{
		div{
			background-color: red;
			font-family: Verdana;
			font-family: 12px;
		}
	}
	@media print{
		div{
			font-family: Arial;
			font-family: 16px;
		}
	}

	/*or*/
	@media screen,print{
		div{
			background-color: red;
			font-family: Arial;
			font-family: 16px;
		}
	}

`max-width` & `min-width` queries = viewport (inner browser window) width

You can define ranges
	
	@media screen and (min-width:400px) and (max-width:800px){

####device metrics

With `max-device-width` and `min-device-width` you can create styles depending on the users screen

---

`orientation` : `portrait` | `landscape`

---

Target specific aspect ratios

	min-aspect-ratio : 4/3
	max-aspect-ratio : 16/9

and
	
	min-device-aspect-ratio : 4/3
	max-device-aspect-ratio : 16/9

---

#####example

	<link type="text/css" rel="stylesheet" media="all and (orientation:portrait)" href="portrait.css"/>
	<link type="text/css" rel="stylesheet" media="all and (orientation:landscape)" href="landscape.css"/>
	<style type="text/css">
		*{
			-webkit-box-sizing: border-box;
			-moz-box-sizing: border-box;
			box-sizing: border-box;
		}
		div{
			float: left;
			height: 200px;
			background-color: red;
			border:1px solid black;
		}
	</style>

##CSS selectors

###descendency selectors

			html
		/			\
	head 			body
				/			\
			div.first 	div.second
			/	|	\	/	|	\
			a 	a 	a 	a 	a 	a

	div.first a { /*descendecy selector*/
		color: #123456;
	}
	div.second a { /*descendecy selector*/
		color: #654321;
	}

###child selector
direct child selector

	div > div{
		color:#facaca;
	}

it is more specific than the descendecy selector

###first child
targets the first child, independently to the elements selector
	
	body > *:first-child{
		color:cacca;
	}

###Adjacent sibling selector

HTML

	<div>
		<p>1</p>
		<p>2</p>
	</div>
	<div>
		<p>3</p>
		<p>4</p>
	</div>
	<div>
		<div>5</div>
		<p>this will be coloured red</p>
	</div>

CSS

	div + p{
		color: red;
	}

###Attribute selector

HTML
	
	<div title="test">
		color red;
	</div>
	<div></div>

CSS
	
	/*targets all divs with title attribute set(also empty)*/
	div[title]{
		color:red;
	}

####regex like attribute selectors

#####exact match

	div[title="test"]{}

#####contains (exact match)

	div[title~="test"]{}

This selects elements which have `test`  inside their title attribute, but whitespace is important (will match `test` but not `teststring` or `test-string`) 

####contains (loose match)

	div[title*="test"]{}

Matches also the other cases above

#####starts with

	div[title^="test"]{}

#####ends with

	div[title$="test"]{}

####lang selector

Not used very often...

	div:lang(de){}

###child selectors

	p:first-child{}
	
	p:last-child{}
	
	p:only-child{}
	
	/*targets every p that is a direct child and happens to be second in the tree*/
	div > p:nth-child(2){}
	
	/*targets elements in the reverse order following the same principle as nth-child*/
	div > p:nth-last-child(2){}
###empty selector

	div:empty{}

targets **empty** elements

	<div></div> <!--is targeted-->
	<div>  </div> <!--is NOT targeted-->

###:not selector

[check the reference](https://developer.mozilla.org/en-US/docs/Web/CSS/:not?redirectlocale=en-US&redirectslug=CSS%2F%3Anot)

##CSS transforms

all these properties remain in the document flow (static), only the presentation layer is modified.

	transform: rotate(30deg);
	transform: scale(2,4); /*scale 2x hor, 4x vert*/
	transform: translate(50px,100px);
	transform: skew(10deg,20deg);

##CSS transitions

You can specifiy which properties you would like to 'animate'/animate their transition

**Warning** Vendor prefixes!

	.test{
		-webkit-transition: -webkit-transform 2s, transform 2s, height 2s;
		-moz-transition: -webkit-transform 2s, transform 2s, height 2s;
		-ms-transition: -webkit-transform 2s, transform 2s, height 2s;
		-o-transition: -webkit-transform 2s, transform 2s, height 2s;
		transition: -webkit-transform 2s, transform 2s, height 2s;
	}
	.test:hover{
		height: 300px;
		-webkit-transform: rotate(10deg);
		-moz-transform: rotate(10deg);
		-ms-transform: rotate(10deg);
		-o-transform: rotate(10deg);
		transform: rotate(10deg);
	}

##CSS animations

Assign animations to an element

	-webkit-animation: my_animation_name 4s ease;
	   -moz-animation: my_animation_name 4s ease;
	    -ms-animation: my_animation_name 4s ease;
	     -o-animation: my_animation_name 4s ease;
	        animation: my_animation_name 4s ease;

Declare animations in this way
	
	@-webkit-keyframes rot {
		from{}
		to{
			-webkit-transform: rotate(1080deg) scale(1.5);
			        transform: rotate(1080deg) scale(1.5);
		}
	}
	/*repeat for EACH vendor prefix*/


#Web site structure

