# CSS Interview Questions


## Describe different ways to use styles on a web page

- inline css: ```<p style=”font-size: 12px;  color: #000000;”>Test </p>```
- embeded css: 
```  
<head>
<style type=”text/css”>
h2 {
   font-size: 16px;
   color: #2d2d2d;
   font-weight: 900;
}
</style>
</head>
```
- linked css: ```  <link rel=”stylesheet” href=”custom/custom.css” type=”text/css” media=”screen, projection” /> ```
- imported css: either in html or css files ``` @import url(‘/css/typography.css’); ```

## Describe difference between inline element and block element

Block-level elements are large blocks of content like  paragraphs or page divisions. Their most significant characteristic is that they typically are formatted with a line break before and after the element (thereby creating a stand-alone block of content). That is, they take up the width of their containers and can contain other blocks as well as inline elements and text or data.. Some block level elements are : address, div, footer, article, aside, canvas, fieldset, hr, ul, form, p, pre, table, section, ol, etc...

Inline elements: an appear within block-level or other inline elements. They take up the width of their contents. They generally contain only data and other inline elements. By default, inline elements do not begin with new line. Some inline elements are: b, small, i, cite, code, a, button, input, label, select, textarea, img, script.


## Describe browser targeting 

Target ALL VERSIONS of IE
```
<!--[if IE]>
	<link rel="stylesheet" type="text/css" href="all-ie-only.css" />
<![endif]-->
```
Target everything EXCEPT IE
```
<!--[if !IE]><!-->
	<link rel="stylesheet" type="text/css" href="not-ie.css" />
 <!--<![endif]-->
 ```
Target IE 6 ONLY
```
<!--[if IE 6]>
	<link rel="stylesheet" type="text/css" href="ie6.css" />
<![endif]-->
```

## Descrube selectors based on relationships

Selector |    Selects
-|-
A E	|Any E element that is a descendant of an A element (that is: a child, or a child of a child, etc.)
A > E|	Any E element that is a child of an A element
E:first-child |	Any E element that is the first child of its parent
B + E  |	Any E element that is the next sibling of a B element (that is: the next child of the same parent)


## Dscribe priority in class and id selectors

You can try rearranging the lines in your CSS file to show that the order has no effect. 
The class selectors .myselector have priority over the tag selector strong, p etc.
The ID selector #myidselector has priority over the class and tag selectors.