# The DOM & jQuery

## Learning Objectives

- Explain what the DOM is and how it is structured
- Target DOM elements using jQuery selectors
- Create, read, update, and delete DOM elements
- Change the attributes or content of a DOM element
- Explain the benefits of jQuery
- Explore jQuery methods for DOM manipulation and traversal

## Framing (10 minutes / 0:10)

In the Objects & Context lesson, you learned about objects as data structures and how we can use them to store data and methods. Today, we will learn about how JavaScript uses objects to represent what you see in the browser.

The [Document Object Model](https://developer.mozilla.org/en-US/docs/Web/API/Document_Object_Model/Introduction), commonly referred to as the "DOM", is a programming interface for HTML. When you load HTML into the browser, it gets converted into a dynamic object-based DOM structure. The [visual representation](https://css-tricks.com/dom/) of this is what you see when you open up Developer Tools in the browser.

The DOM is available for us to manipulate as an object, and this object is structured and stored like an upside down tree, like this...

![lxf118 tut_grease diagram](https://git.generalassemb.ly/storage/user/6376/files/1035f642-6263-11e7-9a38-4db66c999724)

Or this...

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

### The Document Object

Each web page loaded in the browser has its own `document` object. The `document` interface serves as an entry point to the web page's content. The document is an example of an **host object**--that is, a JavaScript object provided by and unique to the browser environment.

### Nodes

Everything in the DOM exists as a **node**. HTML elements are called **element nodes**, attributes are called **attribute nodes**, the text inside elements are called **text nodes**. There are even comment nodes for `<!-- html comments like this one --->`. The document itself is called a document node.

You also can refer to nodes by their relationships to each other. For example, in the graphic above, you would say that the body element is the "parent" to the two `div` elements contained inside it, which are called child nodes. The two divs are also "siblings" to one another because they are on the same level in the tree structure.

Let's look at another example...

![DOM Tree Relationships](http://profsamscott.com/javascript/images/helloworldtree.jpg)

## jQuery Basics (5 minutes / 0:15)

Understanding the DOM is central to working in JavaScript. JavaScript uses the DOM to create dynamic HTML. This includes adding new HTML elements and attributes, changing CSS styles in a page, removing existing elements and attributes, and [many more things](https://www.w3schools.com/js/js_htmldom.asp).

[jQuery](http://api.jquery.com/) is a JavaScript library that is intended to make it easier to use JavaScript to manipulate the DOM. Its motto and guiding principle is "write less, do more".

One of its main features is that it makes selecting DOM elements, DOM traversal (finding HTML elements based on their relationships with other elements), and DOM manipulation much more simple. Another major benefit is that it enables you to write code that behaves the same across different browsers and browser versions.

After working with CSS, you'll find jQuery to be a friendly way to dive into interactive development because it uses a similar syntax for selecting DOM elements.

It's important to note that jQuery **is JavaScript**. Every jQuery method is executing JavaScript code under the hood. You can see this by looking through the [jQuery source code](https://github.com/jquery/jquery/tree/master/src).

### Set Up Environment (5 minutes / 0:20)

```bash
$ git clone https://git.generalassemb.ly/ga-wdi-exercises/jquery-playground.git
$ cd jquery-playground
$ atom .
$ open index.html
```

You can add jQuery to your site by either [downloading it from the jQuery website](https://jquery.com/download/) and hosting it locally or using what's called a Content Delivery Network (CDN). A CDN is a collection of global servers that caches and delivers content including JavaScript files.

Today, we'll use a CDN...

```js
<script src="https://cdnjs.cloudflare.com/ajax/libs/jquery/3.2.1/jquery.js"></script>
```

We're going to add the following code to the top of the `script.js` file when using jQuery...

```js
$(document).ready(function () {
  console.log('hello world')
})
```

> Everything placed inside the `$(document).ready()` method will not be processed until all the HTML has been loaded. In this case, that code is `console.log("hello world")`.

### Selectors (5 minutes / 0:25)

jQuery selectors enable you to find and manipulate HTML elements.

#### Get element by ID

```js
$('#someId')
```

```js
var red = $('#red')
console.log(red)
```

<details>
  <summary><strong>Vanilla JavaScript syntax</strong></summary>

  ```js
  document.getElementById('red')
  ```

</details>

#### Get elements by tag name

```js
$('li')
```

> This will return ***all*** the tags of that name.

```js
var liTags = $('li')
console.log(liTags)
```
<details>
  <summary><strong>Vanilla JavaScript syntax</strong></summary>

  ```js
  document.querySelectorAll('li')
  ```

</details>

#### Get elements by class

```js
$('.myClass')
```

> This will return ***all*** elements with that class.

```js
var liClass = $('.black')
console.log(liClass)
```
<details>
  <summary><strong>Vanilla JavaScript syntax</strong></summary>

  ```js
  document.querySelectorAll('.black')
  ```

</details>

#### All valid CSS selectors and pseudo-selectors work

```js
var lastBlackLi = $('.black:last-of-type')
console.log(lastBlackLi)
```

### Traversal Methods (5 minutes / 0:30)

Once you've made an initial selection, you can dig deeper using traversal methods.

#### `.children()`

```js
var ulChildren = $('ul').children()
console.log(ulChildren)
```

<details>
  <summary><strong>Vanilla JavaScript syntax</strong></summary>

  ```js
  document.querySelector('ul').children
  ```
</details>

#### `.parent()`

```js
var redParent = $('#red').parent()
console.log(redParent)
```
<details>
  <summary><strong>Vanilla JavaScript syntax</strong></summary>

  ```js
  document.getElementById('red').parentNode
  ```

</details>

#### `.siblings()`

```js
var redSiblings = $('#red').siblings()
console.log(redSiblings)
```

#### `.eq()`

```js
var thirdLi = $('li').eq(2)
console.log(thirdLi)
```
<details>
  <summary><strong>Vanilla JavaScript syntax</strong></summary>

  ```js
  document.querySelectorAll('li')[2]
  ```

</details>

## You Do: Selecting DOM elements (30 minutes / 1:00)

> 20 minutes exercise. 10 minutes review.

Spend 20 minutes completing [this exercise](https://git.generalassemb.ly/ga-wdi-exercises/js-dom-quotes/tree/jquery).

## Break (10 minutes / 1:10)

### Get/Set (10 minutes / 1:20)

Many jQuery methods act as both setters and getters for DOM elements, depending on the number of arguments passed in. A **getter** method will return (or "get") the current value of an attribute or property. Think of a getter method as for *reading* a specified property or attribute.  **Setter** methods are used to *write* (or "set") a specified property or attribute.

#### html

The `.html()` method can both retrieve ("get") and change ("set") the HTML contents of a DOM node
- Get: if no argument is passed into the method, it retrieves the HTML content of the first DOM node in the selected collection
- Set: if an argument is passed into the method, it will replace the HTML content of all selected DOM nodes with that argument

```js
// Get
var getInner = $('ul').html()
console.log(getInner)
```

```js
// Set
$('ul').html("<li id='blue'>blue</li>")
```

<details>
  <summary><strong>Vanilla JavaScript syntax</strong></summary>

  ```js
  // Get
  document.querySelector('ul').innerHTML

  // Set
  document.querySelector('ul').innerHTML = "<li class='blue'>Blue</li>"
  ```

</details>

#### `text`

`.text()` is similar to `.html()` except that it will only get / set *text* content (as opposed to HTML content)
- Get: returns the text content of the selected element(s) as a string
- Set: sets the text content of the selected element(s) to whatever is passed in as an argument

```js
// Get
var getText = $('#red').text()
console.log(getText)
```
> Note: unlike `.html()`, if multiple elements are selected, `.text()` will retrieve the text content of *all* of them, not just the first element

```js
// Set
$('li').text('crimson')
```

<details>
  <summary><strong>Vanilla JavaScript syntax</strong></summary>

  ```js
  // To change the text of the first li
  document.querySelector('li').textContent = 'crimson'

  // To change the text of all li's (like `.text()`)
  let lis = document.querySelectorAll('li')
  lis.forEach((li) => li.textContent = 'crimson')
  ```

</details>

#### You Do: Documentation Dive (15 minutes / 1:35)

> 10 minutes exercise. 5 minutes review.

Find a partner, research, and provide an example of getting and setting using the below methods. Be prepared to share your findings with the class.

- `.css()` ([documentation](http://api.jquery.com/css/))
- `.attr()` ([documentation](http://api.jquery.com/attr/))
- `.val()` ([documentation](http://api.jquery.com/val/))

<details>
  <summary><strong>jQuery Solution</strong></summary>

  <strong><code>css</code></strong>

  ```js
  // Get
  var bodyBackgroundColor = $('body').css('background-color')
  console.log(bodyBackgroundColor)
  ```

  ```js
  // Set
  $('body').css('background-color', 'lemonchiffon')
  ```

  <strong><code>attr</code></strong>

  <code>.attr()</code> is use to get/set the value of HTML attributes
  - Get: returns the value of an attribute for the first element in the set of matched elements
  - Set: set the value of an element attribute

  ```js
  // Get
  var imgSrc = $('img').attr('src')
  console.log(imgSrc)
  ```

  ```js
  // Set
  $('img').attr('src','http://www.clipartlord.com/wp-content/uploads/2014/05/unicorn4.png')
  ```

  <strong><code>val</code></strong>

  ```html
  <input type="text" value="Andrew Whitley">
  ```

  ```js
  // Get
  var myName = $('input').val()
  console.log(myName)
  ```

  ```js
  // Set
  $('input').val('Andy Whitley')
  ```

</details>

<details>
  <summary><strong>Vanilla JavaScript Solution</strong></summary>

  ```js
  // Get CSS Property
  document.querySelector('body').style.backgroundColor

  // Set CSS Property
  document.querySelector('body').style.backgroundColor = 'lemonchiffon'
  ```

  ```js
  // Get HTML Attribute
  document.querySelector('img').getAttribute('src')

  // Set HTML Attribute
  document.querySelector('img').setAttribute('src', 'http://www.clipartlord.com/wp-content/uploads/2014/05/unicorn4.png')
  ```

  ```js
  // Get HTML Value
  document.querySelector('input').value

  // Set HTML Value
  document.querySelector('input').value = 'Andrew Whitley'
  ```

</details>

### Adding Content (5 minutes / 1:40)

#### `.append()`

Adds an element to the end of a parent element, making it the last child.

```js
var blue = $('<li>blue</li>')
$('ul').append(blue)
```

<details>
  <summary><strong>Vanilla JavaScript syntax</strong></summary>

  ```js
  var blue = document.createElement('li')
  blue.innerHTML = 'blue'
  document.querySelector('ul').appendChild(blue)
  ```

</details>

#### `.prepend()`

Adds element to the start of a parent element, making it the first child.

```js
$('ul').prepend("<li id='blue'>blue</li>")
```
<details>
  <summary><strong>Vanilla JavaScript syntax</strong></summary>

  ```js
  var blue = document.createElement('li')
  blue.innerHTML = 'blue'
  var refChild = document.querySelector('ul').children[0]
  document.querySelector('ul').insertBefore(blue, refChild)
  ```

</details>

#### You Do: Document Dive (10 minutes / 1:50)

> 5 minutes exercise. 5 minutes review.

Find a partner, research and provide an example for each of the below methods. Be prepared to share your answer.

- `.prependTo()` ([documentation](http://api.jquery.com/prependTo/))
- `.appendTo()` ([documentation](http://api.jquery.com/appendTo/))

### Removing/Showing/Hiding Content (5 minutes / 1:55)

#### `remove`

Removes element from DOM.

```js
$('#red').remove()
```

<details>
  <summary><strong>Vanilla JavaScript syntax</strong></summary>

  ```js
  document.getElementById('red').remove()
  ```

</details>

#### `.empty()`

Removes all the child elements of the jQuery object it is called on.

```js
$('ul').empty()
```

#### `.hide()`

Changes elements style to have `display: none`

```js
$('#red').hide()
```

<details>
  <summary><strong>Vanilla JavaScript syntax</strong></summary>

  ```js
  document.getElementById('red').style.display = 'none'
  ```

</details>

#### `.show()`

Changes a `display: none` to `display: block` or whatever it was initially.

```html
<li id="red" style="display: none;">red</li>
```

```js
$('#red').show()
```

<details>
  <summary><strong>Vanilla JavaScript syntax</strong></summary>

  ```js
  document.getElementById('red').style.display = 'initial'
  ```

</details>

#### You Do: Document Dive (10 minutes / 2:05)

> 5 minutes exercise. 5 minutes review.

For the remaining three methods, find a partner, research and provide an example for each. Be prepared to share your answer.

- `.addClass()` ([documentation](http://api.jquery.com/addClass/))
- `.removeClass()` ([documentation](http://api.jquery.com/removeClass/))
- `.toggleClass()` ([documentation](http://api.jquery.com/toggleClass/))

## You Do: Logo Hijack (15 minutes / 2:20)

> 10 minutes exercise. 5 minutes review.

1. Open up the [Microsoft website](https://www.microsoft.com/en-us/) in Chrome or Firefox, and open the console
2. [Find an image url](https://www.google.com/search?biw=1280&bih=616&tbm=isch&sa=1&q=apple+logo&oq=apple+logo&gs_l=img.3...0.0.0.4212.0.0.0.0.0.0.0.0..0.0....0...1c..64.img..0.0.0.aMLEWJont34) for the apple logo
3. Store the url to the apple logo in a variable
4. Find the Microsoft logo using JavaScript and store it in a variable
5. Modify the source of the logo image so that it's an Apple logo instead
6. Find the Microsoft search input and store it in a variable
7. Modify the placeholder of the input so that it says "Search Apple" instead

#### Bonus

Add a new item to the navigation between the image and the search box. It should contain the text "Apple is the new Microsoft".

## `.each`

With jQuery we might want to do something to each element. Say we have 5 paragraph tags in our html...

```html
<p>Paragraph #1</p>
<p>Paragraph #2</p>
<p>Paragraph #3</p>
<p>Paragraph #4</p>
<p>Paragraph #5</p>
```

Say we wanted to add a class to each paragraph. We can do something like this...

```js
$('p').addClass('pizza')
```

This add the class of `pizza` to each of the paragraph tags. This is happening through something called "implicit iteration" in jQuery. Under the hood JavaScript is looping through each paragraph tag and adding a class. What if we wanted to log the HTML to the console? We might try this...

```js
console.log($('p').html())
```

Hmm, that only gives us the first paragraph's HTML. We need a way to iterate over each of the paragraph tags. Enter `.each`...

```js
$('p').each(function () {
  console.log($(this).html())
})
```
