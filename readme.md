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

## We Do: Set up environment

Make a directory in your sandbox with an `index.html` and a `script.js` file. Then link your `script.js` to your `index.html`.

You can add jQuery to your site by either downloading the file from the jQuery website and hosting locally or using what's called a Content Delivery Network (CDN). A CDN is a collection of global servers that caches and delivers content including Javascript files.

Here, we'll use the Google CDN:

```js
<script src="https://ajax.googleapis.com/ajax/libs/jquery/1.12.4/jquery.min.js"></script>
```

Be sure to put this in before your custom js file so your file can use the library.

You'll then include jQuery's Document Ready event in the `script.js` file. This is another way to ensure that your page loads before any jQuery is executed.

```js

$(document).ready(function(){

   // jQuery goes here...

});
```

### I Do:

I'm going to use jQuery methods to traverse the DOM and turn the text contained in the first list item of an unordered list red. Methods are just functions that are properties of an object.

`index.html`

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <title>Document</title>
</head>
<body>

<ul>
  <li>red</li>
  <li>black</li>
  <li>black</li>
  <li>black</li>
  <li>black</li>
</ul>

<script src="https://ajax.googleapis.com/ajax/libs/jquery/1.12.4/jquery.min.js"></script>
<script src ="script.js"></script>
</body>
</html>
```

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

### You Do: DOM traversal (20 minutes)

Pair up.

(2 minutes)

Write your own code that uses the following jQuery traversal methods. Implement `.eq()` with at least one of these. Adjust HTML accordingly.

  - `.parent()`
  - `.prev()`
  - `.siblings()`
  - `.next()`
  - `.find()`


[ READ THE DOCUMENTATION ](https://api.jquery.com/category/traversing/tree-traversal/)

Incorporate other jQuery methods like I did with `.css()`[Check out this cheat sheet. ](https://oscarotero.com/jquery/)

(15 minutes)

Share! Slack me your code in the discussion channel and let's see how it works.

(5 minutes)

---

Methods are available on any element.

### Methods for selecting elements

- document.getElementById
```js
document.getElementById("someId")
```
- document.getElementsByTagName
```js
document.getElementByTagName("div")
```
- document.getElementsByClassName
```js
document.getElementByClassName("someClass")
```
- document.querySelector
```js
document.querySelector("div#bob h1")
```
- document.querySelectorAll
> `querySelector` and `querySelectorAll` uses CSS selectors in order to select the elements. EX. `document.querySelector("div#bob h1")` This selector would grab the h1 that was a child of a div with id bob.

One thing we can see is that some of these methods return a single DOM object where others return an array of elements.


## You Do: Selecting DOM elements (15 min)

Go to [this repo](https://github.com/ga-wdi-exercises/js-dom-quotes) and follow the instructions in the selecting-dom-elements branch.

Test out grabbing DOM elements using the selectors above.

## Get 'n Set

In programming we'll come across patterns of retrieving information and assigning data relatively frequently. Throughout this course, we'll learn a lot of functionalities across both JS and Ruby that get and set data for us.

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

## You do: Logo hijack (15 min)M

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

## Break (5 min)

## Events (10 min)
Let's take a look at this [site](http://jessicahische.is/). We can click on one of these themes and the webpage seemingly completely changes!

What is an event?
http://eloquentjavascript.net/14_event.html

Events are a way we can add behavior depending on something happening. Think back to cookie clicker. When we click the cookie, something happens.

Lets write some html that contains a couple elements we can click on. Create an `index.html` and put in the following contents:

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <title>Document</title>
</head>
<body>
  <h1>Click Me!</h1>
  <a href="https://www.google.com">This is a link to google!</a>
  <script src="script.js"></script>
</body>
</html>
```

We have an `h1` as well as an `a`. Let's add event listeners for clicking to both.

### Event Listeners for clicking
`addEventListener`
```js
var clickMe = document.querySelector("h1")
clickMe.addEventListener("click", function(){
  console.log("you clicked the h1!")
})
var anchor = document.querySelector("a")
anchor.addEventListener("click", function(){
  console.log("you clicked the anchor!")
})
```

> The first argument for `addEventListener` is the event you are listening for. In this case, the `click` event. The second argument is the thing that should happen when the event occurs, otherwise known as a callback. There's much to learn about `events` and `callbacks`. So much so that we have devoted another entire class to it.. So more to follow!

Hmm, if we click on the link, its still going to google. What gives? Turns out anchors have a default action when we click them. They go to the specified link. We need a way to ignore the default behavior. We can do this by leveraging the event object.

```js
var anchor = document.querySelector("a")
anchor.addEventListener("click", function(evt){
  evt.preventDefault()
  console.log("you clicked the anchor!")
})
```

> There's lots more about events that you'll learn in the next classes. For now, know that every event listener you add allows us the access the event object as an argument of the function callback.

## Exercises

- [Take the Money and Run](https://github.com/ga-wdi-exercises/ttmar)
- [color scheme switcher](https://github.com/ga-wdi-exercises/color-scheme-switcher)


## Homework
Finish [Take the Money and Run](https://github.com/ga-wdi-exercises/ttmar)


## References
- https://developer.mozilla.org/en-US/docs/Web/API/Event

[![Build Status](https://travis-ci.org/ga-wdi-lessons/js-dom.svg?branch=master)](https://travis-ci.org/ga-wdi-lessons/js-dom)
