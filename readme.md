# The DOM (Document Object Model) & JQuery Basics

## Learning Objectives

- Explain what the DOM is and how it is structured
- Select and target DOM elements using DOM methods
- Select and target DOM elements using a query selector
- Create, read, update, and delete DOM elements
- Change the attributes or content of a DOM element

## Framing (5 min)

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

## JQuery Basics

Understanding the DOM is central to working in Javascript. Essentially, Javascript uses the DOM to create dynamic HTML.[ This includes](hhttp://www.w3schools.com/js/js_htmldom.asp) adding new HTML elements and attributes, changing CSS styles in a page and removing existing elements and attributes.

JQuery is a Javascript library that is intended to make it easier to use Javascript on your website. It's known as the "write less, do more" library. One of its main features is that it makes DOM traversal--that is, finding HTML elements based on its relationships to other elements--and DOM manipulation much more simple. Another major benefit is that it enables you to write code that behaves the same across different browsers and browser versions.

## We Do: Set up environment (5 minutes)

Make a directory in your sandbox with an `index.html` and a `script.js` file. Then link your `script.js` to your `index.html`.

You can add jQuery to your site by either downloading the file from the jQuery website and hosting locally or using what's called a Content Delivery Network (CDN). A CDN is a collection of global servers that caches and delivers content including Javascript files.

Here, we'll use the Google CDN:

```js
<script src="https://ajax.googleapis.com/ajax/libs/jquery/2.2.4/jquery.min.js"></script>
```

Be sure to put this in before your custom js file so your file can use the library.

You'll then include jQuery's Document Ready event in the `script.js` file. This is another way to ensure that your page loads before any jQuery is executed.

Here's what your `script.js` should look like to start:

```js

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
- Getting an element by its tag name
```js
$( "div" )
```
- Getting an element by its Class
```js
$( ".myClass" )
```
[ Read about more here ](https://api.jquery.com/category/traversing/tree-traversal/)

### Traversal Methods

Once you've made an initial selection, you can dig deeper using traversal methods.

`.children()`

*Example*
```js
var ulChildren = $( "ul" ).children();
console.log(ulChildren);
```
- `.parent()`
- `.siblings()`

[ Read about more here ](https://api.jquery.com/category/traversing/tree-traversal/)

## Get/Modify content

- _element_`.innerHTML()` [documentation](https://developer.mozilla.org/en-US/docs/Web/API/Element/innerHTML)
  - get or set the HTML contents **can also be used to add HTML elements**
  - get: no argument, know that it returns everything between the tags of the specified element

  ```javascript
  var currentContent = element.innerHTML
  // currentContent contains all of the elements children
  ```

    - set: one argument that you want the html content to be

  ```javascript
  element.innerHTML = newContent
  // removes all of the elements children and replaces with whatever newContent is
  ```

- _element_`.textContent` [documentation](https://developer.mozilla.org/en-US/docs/Web/API/Node/textContent)
  - similar to innerHTML except that it will not turn markup into elements and will keep strings intact

  ```javascript
  var text = element.textContent;
  // returns the content of the selected element as a string, and store it in the variable `text`
  element.textContent = newContent;
  // removes all of the elements children and replaces with whatever newContent is
  ```

- _element_`.style.<propertyName>` [documentation](https://developer.mozilla.org/en-US/docs/Web/API/HTMLElement/style)
  - used to set and modify CSS properties, where `<propertyName>` is the name of the desired CSS attribute to get or set

  ```js
  var currentValue = element.style.backgroundColor;
  // will return what the current backgroundColor of the selected element, and store it in the variable `currentValue`

  element.style.height = someNewValue;
  // will set the height of the selected element to whatever someNewValue is
  ```

Add an input tag to the `index.html`:

```html
<input type="text" class="search" placeholder="some text here ....">
```

- _element_`.value` [documentation](https://developer.mozilla.org/en-US/docs/Web/API/HTMLInputElement)
  - only works for input tags - gets current value in the input

> We need to be able to get information from users. Input tags are a great way to do that. But more importantly we need to be able to access those values so that our JS can act on it. Think about auto complete on search forms. As we type something into google, it starts giving us options. For every key stroke we make, the callback that is fired is probably using some form of `.value`. This will also be extremely important moving forward in week 7 with AJAX.

## Adding content

- `document.createElement(tagName)` [documentation](https://developer.mozilla.org/en-US/docs/Web/API/Document/createElement)
  - creates the specified HTML tag

  ```js
  var element = document.createElement('div');
  // will return a created div and store it in the variable element
  ```

- _element_`.appendChild()` [documentation](https://developer.mozilla.org/en-US/docs/Web/API/Node/appendChild)
  - adds a node to the end of the lis of children of a specified parentNode

  ```js
  var child = element.appendChild(newChildElement);
  // appends the newChildElement as a child of element, stores this in the variable child
  ```

- _element_`.insertBefore(newNode, referenceNode)` [documentation](https://developer.mozilla.org/en-US/docs/Web/API/Node/insertBefore)
  - inserts the specified element before the reference node as a child of the current element

  ```js
  var insertedNode = parentNode.insertBefore(newNode, referenceNode);
  ```

  > Think about how facebook statuses work. When we add a new status, does it go to the bottom of the list? or is it right at the top? Maybe they're using a prepend here ...

## Removing content

- _element_`.removeChild()` [documentation](https://developer.mozilla.org/en-US/docs/Web/API/Node/removeChild)

- _element_`.innerHTML = ''`
  - can be used to replace all of the contents of an element with nothing (an empty string) - see above description for usage


## I Do: Putting it all together (5 minutes)

I'm going to use jQuery methods to traverse the DOM and turn the text contained in the first list item of an unordered list red. Methods are just functions that are properties of an object.

`script.js`

```js
$(document).ready(function(){

// selected the ul tag
// .children alone selects all child elements
// using .eq reduces the set to a specific index
// the .css method set the color of the text
$("ul").children().eq(0).css( "color", "red" );

});
```

## You Do: Selecting DOM elements (20 min)

Go to [this repo](https://github.com/ga-wdi-exercises/js-dom-quotes) and follow the instructions in the jQuery branch.

Test out grabbing DOM elements using the selectors above.

## Get 'n Set

In programming, we'll come across patterns of retrieving information and assigning data relatively frequently. Throughout this course, we'll learn a lot of functionalities across both JS and Ruby that get and set data for us.

Try accessing DOM elements leveraging the selector methods above.

## Altering DOM Elements (5 min)

- [.textContent](https://developer.mozilla.org/en-US/docs/Web/API/Node/textContent)
- .innerHTML
  this is used as both a getter and setter method

  Getter:
  ```js
  document.querySelector("someElement").innerHTML
  ```

  Setter:
  ```js
  document.querySelector("someElement").innerHTML = "the text that will be inserted for that element"
  ```

- .setAttribute(name, value);
  Ex:
  ```js
  document.querySelectorAll("img").setAttribute("src", "www.someImageURL.com")
  ```

  > sets all images to have the source of `"www.someImageURL.com"`

- .id
  sets or gets an ID for a DOM element

- .style
  Getter:
  ```js
  document.querySelector("someElement").style.background
  ```

  Setter:
  ```js
  document.querySelector("someElement").style.background = "blue"
  ```

> Note: these are just some snippets, read the full [MDN DOM documentation](https://developer.mozilla.org/en-US/docs/Web/API/Document_Object_Model) for more examples

## You do: Logo hijack (15 min)

1. Open up www.google.com in Chrome or Firefox, and open up the console.
- find an image url for the yahoo logo
- Store the url to the Yahoo logo in a variable.
- Find the Google logo using JS and store it in a variable.
- Modify the source of the logo IMG so that it's a Yahoo logo instead.
- Find the Google search button and store it in a variable.
- Modify the text of the button so that it says "Yahooo!" instead.

Bonus: Add a new element between the image and the search textbox, telling the world that "Yahoo is the new Google".

## Creating/Removing DOM Elements (1 min)

- [document.createElement](https://developer.mozilla.org/en-US/docs/Web/API/Document/createElement)

```js
var newDiv = document.createElement("div")
newDiv.innerHTML = "Whoa, this is created from JS!"
```

- [Node.appendChild](https://developer.mozilla.org/en-US/docs/Web/API/Node/appendChild)

```js
document.body.appendChild(newDiv)
```
- Node.removeChild

## Exercises

- [Take the Money and Run](https://github.com/ga-wdi-exercises/ttmar)
- [color scheme switcher](https://github.com/ga-wdi-exercises/color-scheme-switcher)


## Homework
Finish [Take the Money and Run](https://github.com/ga-wdi-exercises/ttmar)


## References
- https://developer.mozilla.org/en-US/docs/Web/API/Event

[![Build Status](https://travis-ci.org/ga-wdi-lessons/js-dom.svg?branch=master)](https://travis-ci.org/ga-wdi-lessons/js-dom)
