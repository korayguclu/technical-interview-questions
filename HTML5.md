# HTML5 Interview Questions

## What is HTML5?


HTML5 was specially designed to deliver rich content without the need for additional pluginssuch as animation to graphics, music to movies, and can also be used to build complicated web applications. HTML5 is cross platform all major browsers are supporting HTML5.

## What doctype do you need for HTML5

Followin doctype is the only one that you need.
```
<!DOCTYPE html>
```
If you donot use this tag, HTML5 Tags will not work properly. 
Following code show a HTML5 document
```
<!DOCTYPE html>
<html>
<head>
<meta charset="UTF-8">
<title>Title</title>
</head>
<body>
Content...
</body>
</html>
```

## Describe HTML5 Tags for Page Structure

Following tags are HTML5 tags which are used to structure a page.

- header: Represents header data of HTML.
- footer: Footer section of the page.
- nav: Navigation elements in the page.
- article: Self-contained content.
- section: Used inside article to define sections or group content in to sections.
- aside: Represent side bar contents of a page.

## Describe HTML5 Datalist

Datalist provides autocomplete features for textboxs.

```
<input list="Country">
<datalist id="Country">
<option value="Germany">
<option value="Japan">
<option value="USA">
<option value="England">
</datalist> 
```
## Describe some HTML5 form elements

Some of the important form elements are : Color,Date,Datetime-local,Email,Time,Url,Range,Telephone,Number,Search
For example if you want to show color picker you can use

```
<input type="color" name="color_selection">  
```

## Describe canvas in HTML5

Canvas is an HTML area where you can draw graphics.

## Describe LocalStorage in HTML5

HTML is stateless. There may be times when you want to store users state. One option is Cookies. But Cookies has certain limitations e.g. 4KB limit. HTML5 compable browsers provides a solution for this, which allows to keep a key on the user’s computer and read it out when the user returns.

It is easy to use localStroage on HTML5 Browsers. All you have to do is use setItem() getItem methods in localStorage object. You can store variables or objects.

```
localStorage.setItem('myemail','alfrad@example.org');
var email = localStorage.getItem('myemail');
```

Local storage does not have a life time it will stay until either the user clear it from the browser or you remove it using JavaScript code as follows.

```
localStorage.removeItem('myemail' );

```

## Describe sessionStorage 

sessionStorage is like localStorage but in constrast to localStorage data to be maintained only until the browser window closes.
localStorage does not have a life time limit.

## Decribe HTML5 shim/shiv and modernizer 

HTML5 shim/shiv or Modernizr.js renders HTML5 elements correctly in Internet Explorer prior to version 9.

## Describe HTML5 shim/shiv and its usage 

HTML5Shiv is a JavaScript workaround solution to display HTML5 elements properly in versions of Internet Explorer prior to version 9. IE 8 and less do not allow unknown elements to be styled without JavaScript.

It does not suddenly make older IE Browsers support the audio or video element, it just means that you can use section instead of div and style them in CSS.

Insert following code in your head tag.

```
<!--[if lt IE 9]>
<script src="dist/html5shiv.js"></script>
<![endif]-->
```

## Describe difference between HTML5 Shim/shiv and Modernizr

Modernizr 1.5+ 


## Describe Media Queries 

HTML 5 Media Queries are allowing content rendering to adapt to conditions such as screen resolution such as smartphone or web monitor resolution.


## Which HTML 4.0 elements are removed in HTML5

Follown elements have been removed : acronym, applet, basefont, big, center, dir, font, frame, frameset, noframes, strike, tt 

## Describe CSS Reset and normalize.css

Every browser has its own default stylesheet,that it uses to make unstyled websites appear better.
A CSS Reset  minified set of CSS rules that resets the styling of all HTML elements to a consistent baseline to remove differences between browsers.

Normalize.css is a such CSS reset library.  

# HTML5 Links

- http://caniuse.com/
- http://html5test.com/
- http://fmbip.com/litmus
- http://htmldog.com/