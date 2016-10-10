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

Understanding the DOM is central to working in Javascript. Essentially, Javascript uses the DOM to create dynamic HTML.[ This includes](http://www.w3schools.com/js/js_htmldom.asp) adding new HTML elements and attributes, changing CSS styles in a page and removing existing elements and attributes.

JQuery is a Javascript library that is intended to make it easier to use Javascript on your website. It's known as the "write less, do more" library. One of its main features is that it makes DOM traversal--that is, finding HTML elements based on its relationships to other elements--and DOM manipulation much more simple. Another major benefit is that it enables you to write code that behaves the same across different browsers and browser versions.

After working with CSS, you'll find jQuery a friendly way to dive into interactive development because it also emphasizes the use of selecting elements so you can do stuff to them.

It's also important to note that jQuery IS Javascript so it's not accurate to say, if you're so inclined, that 'jQuery is better than Javascript.' You can distinguish the traditional style by calling it vanilla Javascript.

### Set up environment (5 minutes)

A one liner!

```
$ git clone https://github.com/ga-wdi-exercises/jquery-playground.git && cd jquery-playground && atom . && open index.html
```

You can add jQuery to your site by either downloading the file from the jQuery website and hosting locally or using what's called a Content Delivery Network (CDN). A CDN is a collection of global servers that caches and delivers content including Javascript files.

Here, we'll use a CDN:

```js
<script src="https://cdnjs.cloudflare.com/ajax/libs/jquery/3.1.1/jquery.js"></script>
```

We're going to add the following code to the top of every script file when using jquery:

```js
$(document).ready(function(){
  console.log("hello world")
})
```

> `$(document).ready()` is a way we can make sure all of our HTML is loaded first, before we execute any jQuery/JS code. It's leveraging events and callbacks(we'll learn about these in the next lesson). We write the three lines above to ensure we've properly accessed the jQuery library as well as our script file in our HTML so long as we see the "hello world" show up in the console.

#### Note

- Load jquery before your own code
- Load both just before the closing body tag

### Selectors (10 minutes)

jQuery selectors enable you to find and manipulate HTML elements.

#### Getting an element by its Id
```js
$( "#someId" )
```
*Example*
```js
var red = $( "#red" );
console.log(red);
```
<details>
<summary>
Vanilla Javascript syntax
</summary>

```javascript
document.getElementById("red");
```
</details>

#### Getting elements by tag name.
>Notice this will return all the tags of that name.

```js
$( "li" )
```
>Demo in console

*Example*
```js
var liTags = $( "li" );
console.log(liTags);
```
<details>
<summary>
Vanilla Javascript syntax
</summary>

```javascript
document.querySelectorAll("li");
```
</details>

#### Getting elements by Class.

> Again, this will return all elements with that class.

```js
$( ".myClass" )
```
*Example*
```js
var liClass = $( ".black" );
console.log(liClass);
```
<details>
<summary>
Vanilla Javascript syntax
</summary>

```javascript
document.querySelectorAll(".black");
```
</details>

But also any valid CSS selector will work:

```js
var lastBlackLi = $(".black:last-of-type")
console.log(lastBlackLi)
```


### Traversal Methods (10 minutes)

Once you've made an initial selection, you can dig deeper using traversal methods.

#### `.children()`

*Example*
```js
var ulChildren = $( "ul" ).children();
console.log(ulChildren);
```
<details>
<summary>
Vanilla Javascript syntax
</summary>


```javascript
 document.getElementById("red").children
```
</details>

#### `.parent()`

*Example*
```js
var redParent = $( "#red" ).parent();
console.log(redParent);
```
<details>
<summary>
Vanilla Javascript syntax
</summary>


```javascript
document.getElementById("red").parentNode
```
</details>

#### `.siblings()`

*Example*
```js
var redSiblings = $( "#red" ).siblings();
console.log(redSiblings);
```

This above example highlights a very cool feature from jQuery called method chaining. Essentially, this allows us to perform multiple methods on the same set of elements in a single line.

#### `.eq()`

*Example*
```js
var getRed = $( "li" ).eq(0);
console.log(getRed);
```
<details>
<summary>
Vanilla Javascript syntax
</summary>


```javascript
Use []. ex: document.getElementById("myID").childNodes[2]
```
</details>

## Break (10 minutes)


## You Do: Selecting DOM elements (20 min)

[Exercise Here](https://github.com/ga-wdi-exercises/js-dom-quotes/tree/jquery)

### Get/Modify (15 minutes)

In programming, we'll come across patterns of retrieving information and assigning data relatively frequently. Throughout this course, we'll learn a lot of functionalities across both JS and Ruby that get and set data for us.

#### `.html()`
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
  <details>
  <summary>
  Vanilla Javascript syntax
  </summary>


  ```javascript
  document.querySelector("ul").innerHTML = "<li>Blue</li>"
  ```
  </details>

#### `.text()`
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
  <details>
  <summary>
  Vanilla Javascript syntax
  </summary>


  ```javascript
  document.querySelector("ul").textContent = "<li>Blue</li>"
  ```
  </details>

#### `.css()` - You do
- How do you get/set CSS properties on a jQuery object?
- How do you set multiple CSS properties?

#### `.attr()`
- get: returns the value of an attribute for the first element in the set of matched elements
- set: set the value of an element attribute

  *Get Example*
  ```javascript
  var language = $('html').attr('lang')
  console.log(language);
  ```

  *Set Example*
  ```javascript
  $('img').attr('src','http://www.clipartlord.com/wp-content/uploads/2014/05/unicorn4.png')
```

<details>
<summary>
Vanilla Javascript syntax
</summary>


```javascript
.setAttribute();
```
</details>

#### You Do: Document Dive and examples (10 minutes)

For the last method, find a partner, research, and provide an example of getting and setting. Be prepared to share your findings with the class. Create an input tag in your HTML for the `.val()` to work effectively.

```html
<input type="text" value="hello">
```
- `.val()`
[documentation](http://api.jquery.com/val/)

<details>
<summary>
`.val()` example:
</summary>
`html`
```html
<input type="text" value="name">
```

```javascript
$("input").val("Nayana Davis");
// set
```

```javascript
var myName = $("input").val();
console.log(myName)
// get
```
</details>

<details>
<summary>
Vanilla Javascript syntax
</summary>


```javascript
.value
```
</details>

### Adding content (5 minutes)

#### `.append()`
- adds newly created element to the end of a parent element, making it the last child

```javascript
var blue = $( "<li>blue</li>" );
$( "ul" ).append(blue);
```
<details>
<summary>
Vanilla Javascript syntax
</summary>


```javascript
.appendChild()
```
</details>

#### `.prepend()`
- adds newly created element to the start of a parent element, making it the first child

```javascript
$( "ul" ).prepend( "<li>pink</li>" );
```
<details>
<summary>
Vanilla Javascript syntax
</summary>


```javascript
.insertBefore()
```
</details>

#### You Do: Document Dive and examples (10 minutes)

For the remaining two methods, find a partner, research and provide an example for each. Be prepared to share your answer.

- `.prependTo()`
[documentation](http://api.jquery.com/prependTo/)
- `.appendTo()`
[documentation](http://api.jquery.com/appendTo/)


### Removing content (5 minutes)

#### `.remove()`
- removes element from DOM

```javascript
$( "#red" ).remove();
```
<details>
<summary>
Vanilla Javascript syntax
</summary>
```javascript
.removeChild()
```
</details>

#### `.empty()`
- removes all the child elements of the jquery object it is called on

```javascript
$( "ul" ).empty();
```

### Others (5 minutes)

#### `.hide()`
changes elements style to have `display:none`

 ```javascript
 $( "#red" ).hide();
 ```

#### `.show()`
changes a `display:none` to `display:block` or whatever it initially was

```html
<li id ="red" style ="display:none">red</li>
```

```javascript
$( "#red" ).show();
```

#### You Do: Document Dive and examples (10 minutes)

For the remaining three methods, find a partner, research and provide an example for each. Be prepared to share your answer.

   `.addClass()`
   [documentation](http://api.jquery.com/addClass/)

   `.removeClass()`
   [documentation](http://api.jquery.com/removeClass/)

   `.toggleClass()`
   [documentation](http://api.jquery.com/toggleClass/)

## You do: Logo hijack (15 min)

1. Open up https://www.microsoft.com/en-us/ in Chrome or Firefox, and open up the console.
1. find an image url for the apple logo
1. Store the url to the apple logo in a variable.
1. Find the Microsfot logo using JS and store it in a variable.
1. Modify the source of the logo IMG so that it's an apple logo instead.
1. Find the Microsoft search input and store it in a variable.
1. Modify the placeholder of the input so that it says "Search Apple" instead.

Bonus: Add a new element between the image and the search textbox, telling the world that "Microsoft is the new Apple".

## `.each`

With jquery we might want to do something to each element. Say we have 5 paragraph tags in our html:

```html
<p>paragraph1</p>
<p>paragraph2</p>
<p>paragraph3</p>
<p>paragraph4</p>
<p>paragraph5</p>
```

Say we wanted to add a class to each paragraph. We can do something like this:

```js
$("p").addClass("pizza")
```

And this would go ahead and add the class of `pizza` to each of the paragraph tags. This is happening through something called implicit iteration in jQuery. Under the hood its looping through each paragraph tag and adding a class. What if we wanted to log the html to the console? We might try this:

```js
console.log($("p").html())
```

Hmm, that only gives us the first paragraph tags html. Whelp, we need a way to iterate over each of the paragraph tags. Enter `.each`:

```js
$("p").each(function(){
  console.log($(this).html())
})
```

## You do TTMAR

Try out [click events](http://api.jquery.com/on/#event-handler)!

https://github.com/ga-wdi-exercises/ttmar
