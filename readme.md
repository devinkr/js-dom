# The DOM (Document Object Model) & JQuery Basics

## Learning Objectives

- Explain what the DOM is and how it is structured
- Select and target DOM elements using DOM methods
- Select and target DOM elements using a query selector
- Create, read, update, and delete DOM elements
- Change the attributes or content of a DOM element
- Explain the benefits of jQuery
- Explore jQuery methods for DOM manipulation and traversal

## Intro (5 minutes)

We learned some things about JS objects. We learned that we can give objects key value pairs to program logic from real life objects. Turns out, we can actually treat elements in our HTML as objects in our JS programs.

The [**D**ocument **O**bject **M**odel](https://developer.mozilla.org/en-US/docs/Web/API/Document_Object_Model/Introduction)
is a programming interface for HTML. When you load HTML into the browser, it gets converted into a DOM structure. The [ visual representation](https://css-tricks.com/dom/) of this is what you see when you open up Developer Tools in the browser.

[ Read this](https://css-tricks.com/dom/) to learn more about the DOM.

*(3 minutes)*

We're used to seeing our HTML displayed in the browser, but now we're going to think more about how it gets stored in memory.

An HTML *document* is available for us to manipulate as an object, and this object is structured and stored like an upside down tree:

Like this:

![](http://www.tuxradar.com/files/LXF118.tut_grease.diagram.png)

Or this:

```
html
└── head
│   ├──title
│   ├──meta
│   ├──link[rel="stylesheet"]
|   └──script[type="text/javascript"]
|
└── body
    ├── header
    │   ├── h1
    │   └── nav
    └── section.simplicity
    |   └── h2
    │   └── article
    ├── section.life
    |   └── h2
    │   └── article
    │       └── block_quote
    │       └── block_quote
    └── footer
```


Let's look at the structure of [a page](https://github.com/ga-wdi-exercises/js-dom-quotes/blob/master/index.html)

## The Document Object (5 min)

Each web page loaded in the browser has its own `document` object. The `document` interface serves as an entry point to the web page's content. The document is an example of a *host object*--that is, an object provided to Javascript by the browser environment.

## Nodes (5 minutes)

Everything in the HTML DOM is called a node. Elements are called element nodes, attributes are called attribute nodes, the text inside elements are called text nodes. There are comment nodes. The document itself is called a document node.

You also can refer to nodes by their relationships to each other. For example, in the graphic above, you would say that the body element is the parent to the two div elements contained inside it, which are called child nodes. The two divs are also siblings to one another because they are on the same level in the tree structure.

Let's look at another example:


![](http://www.dege.ukfsn.org/dom/dom.gif)

## JQuery Basics (5 minutes)

Understanding the DOM is central to working in Javascript. Essentially, Javascript uses the DOM to create dynamic HTML.[ This includes](hhttp://www.w3schools.com/js/js_htmldom.asp) adding new HTML elements and attributes, changing CSS styles in a page and removing existing elements and attributes.

JQuery is a Javascript library that is intended to make it easier to use Javascript on your website. It's known as the "write less, do more" library. One of its main features is that it makes DOM traversal--that is, finding HTML elements based on its relationships to other elements--and DOM manipulation much more simple. Another major benefit is that it enables you to write code that behaves the same across different browsers and browser versions.

After working with CSS, you'll find jQuery a friendly way to dive into interactive development because it also emphasizes the use of selecting elements so you can do stuff to them.

It's also important to note that jQuery IS Javascript so it's not accurate to say, if you're so inclined, that 'jQuery is better than Javascript.' You can distinguish the traditional style by calling it vanilla Javascript.

## We Do: Set up environment (5 minutes)

Make a directory in your sandbox with an `index.html` and a `script.js` file. Then link your `script.js` to your `index.html`.

You can add jQuery to your site by either downloading the file from the jQuery website and hosting locally or using what's called a Content Delivery Network (CDN). A CDN is a collection of global servers that caches and delivers content including Javascript files.

Here, we'll use the Google CDN:

```js
<script src="https://ajax.googleapis.com/ajax/libs/jquery/2.2.4/jquery.min.js"></script>
```

Be sure to put this in before your custom js file so your file can use the library.

You'll then include jQuery's Document Ready event in the `script.js` file. This is another way to ensure that your page loads before any jQuery is executed. Code contained inside the Document Ready will only run once jQuery detects that the DOM is "ready". It's best practice to include this in every jQuery script you write.

Here's what your `script.js` should look like to start:

```js

// below is the standard code for the document ready event.
$(document).ready(function(){

   // jQuery goes here...

});
```
And here's how our `index.html` should look:

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <title>Document</title>
</head>
<body>

<ul>
  <li id ="red">red</li>
  <li class ="black">black</li>
  <li class ="black">black</li>
  <li class ="black">black</li>
  <li class ="black">black</li>
</ul>

<script src="https://ajax.googleapis.com/ajax/libs/jquery/2.2.4/jquery.min.js"></script>
<script src ="script.js"></script>
</body>
</html>
```


### Selectors

jQuery selectors enable you to find and manipulate HTML elements.

- Getting an element by its Id
```js
$( "#someId" )
```
*Example*
```js
var red = $( "#red" );
console.log(red);
```
- Getting elements by tag name. Notice this will return all the tags of that name.
```js
$( "li" )
```

*Example*
```js
var liTags = $( "li" );
console.log(liTags);
```
- Getting elements by Class. Again, this will return all elements with that class.
```js
$( ".myClass" )
```
*Example*
```js
var liClass = $( ".black" );
console.log(liClass);
```
- You can also combine elements to



### Traversal Methods

Once you've made an initial selection, you can dig deeper using traversal methods.

`.children()`

*Example*
```js
var ulChildren = $( "ul" ).children();
console.log(ulChildren);
```
`.parent()`

*Example*
```js
var redParent = $( "#red" ).parent();
console.log(redParent);
```
- `.siblings()`

*Example*
```js
$( "#red" ).siblings().css("color","green");
console.log(redSiblings);
```
This above example highlights a very cool feature from jQuery called method chaining. Essentially, this allows us to perform multiple methods on the same set of elements in a single line.

- `.eq()`

*Example*
```js
var getRed = $( "li" ).eq(0);
console.log(getRed);
```


## You Do: Selecting DOM elements (20 min)

Go to [this repo](https://github.com/ga-wdi-exercises/js-dom-quotes) and follow the instructions in the jQuery branch.

Test out grabbing DOM elements using the selectors above.

### Get/Modify

In programming, we'll come across patterns of retrieving information and assigning data relatively frequently. Throughout this course, we'll learn a lot of functionalities across both JS and Ruby that get and set data for us.

`.html()`
- get or set the HTML contents
- get: no argument, know that it returns the innerHTML of the first jQuery object
- set: one argument that you want the html content to be

  *Get Example*

  ```javascript
  var getInner = $( "#red" ).html();
  console.log(getInner);
  ```

  *Set Example*
  ```javascript
  $( "ul" ).html("<li>blue</li>");
  ```

`.text()`
  - similar to `.html()`except that it will not turn markup into elements and will keep strings intact

  - get: returns the content of the selected element as a string, and store it in the variable `text`
  - set: removes all of the elements children and replaces with whatever newContent is


  *Get Example*
  ```javascript
  var getText = $( "ul" ).text();
  console.log(getText);
```
  *Set Example*
  ```javascript
  $( "ul" ).text("<li>blue</li>");
  ```


`.attr()`
- get: returns the value of an attribute for the first element in the set of matched elements
- set: set the value of an element attribute

  *Get Example*
  ```javascript
  var getAttr = $('html').attr('lang')
  console.log(getAttr);
  ```

  *Set Example*
  ```javascript
  var setAttr = $('img').attr('src','http://www.clipartlord.com/wp-content/uploads/2014/05/unicorn4.png')
```

####You Do: Document Dive and examples (10 minutes)

For the last method, find a partner, research, and provide an example of getting and setting. Be prepared to share your findings with the class. Create an input tag in your HTML for the `.val()` to work effectively.

```html
<input type="text" value="hello">
```
- `.val()`
[documentation](http://api.jquery.com/val/)


### Adding content

`.append()`
- adds newly created element to the end of a parent element, making it the last child

```javascript
var blue = $( "<li>blue</li>" );
$( "ul" ).append(blue);
```

`.prepend()`
- adds newly created element to the start of a parent element, making it the first child

```javascript
$( "ul" ).prepend( "<li>pink</li>" );
```

####You Do: Document Dive and examples (10 minutes)

For the remaining two methods, find a partner, research and provide an example for each. Be prepared to share your answer.

- `.prependTo()`
[documentation](http://api.jquery.com/prependTo/)
- `.appendTo()`
[documentation](http://api.jquery.com/appendTo/)


### Removing content

`.remove()``
- removes element from DOM

```javascript
$( "#red" ).remove();
```

`.empty()`
- removes all the child elements of the jquery object it is called on

```javascript
$( "ul" ).empty();
```

### Others

`.hide()`
 - changes elements style to have `display:none`

 ```javascript
 $( "#red" ).hide();
 ```
 - `.show()`
   - changes a `display:none` to `display:block` or whatever it initially was

   ```html
   <li id ="red" style ="display:none">red</li>
   ```

   ```javascript
   $( "#red" ).show();
   ```

####You Do: Document Dive and examples (10 minutes)

For the remaining two methods, find a partner, research and provide an example for each. Be prepared to share your answer.

   `.addClass()`
   [documentation](http://api.jquery.com/addClass/)

   `.removeClass()`
   [documentation](http://api.jquery.com/removeClass/)

## You do: Logo hijack (15 min)

1. Open up www.google.com in Chrome or Firefox, and open up the console.
- find an image url for the yahoo logo
- Store the url to the Yahoo logo in a variable.
- Find the Google logo using JS and store it in a variable.
- Modify the source of the logo IMG so that it's a Yahoo logo instead.
- Find the Google search button and store it in a variable.
- Modify the text of the button so that it says "Yahooo!" instead.

Bonus: Add a new element between the image and the search textbox, telling the world that "Yahoo is the new Google".

[![Build Status](https://travis-ci.org/ga-wdi-lessons/js-dom.svg?branch=master)](https://travis-ci.org/ga-wdi-lessons/js-dom)
