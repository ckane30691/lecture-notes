# Let's talk about JavaScript!
---
# JavaScript Wat
https://www.destroyallsoftware.com/talks/wat
---
# Today's Topics
- What JavaScript is
- The pieces that make up JavaScript
- Asynchronicity in JavaScript
- Some trivia
Note:
Today's goal is become more comfortable with talking about JS, it's parts, and some of it's features, as a whole.
Anything specific that anyone would like to go over?

---

## JavaScript is
#### a high level interpreted programming language.
* Dynamic
* Weakly Typed
* Prototype-Based
* Multi-paradigm
* Single-threaded
* Concurrent
* Never Blocking
Note:
Dynamic (it can execute many common behaviors at runtime rather than having to be compiled)
Weakly Typed (types are not declared or firmly adhered to making things like type coercion possible)
Prototype-Based (OOP style based on sharing behavior through objects or 'prototypes')
Multi-paradigm (permits the use of different programming paradigms)
Single-threaded (it can only execute one action at any given time)
Concurrent (capable of delegating multiple tasks simultaneously)*
Never Blocking (What would be blocking?) (I/O does not interfere with user input and activity)
How can it be concurrent and single threaded??? We'll get to that.

---

##  Concurrent Vs Parallel
note: https://takuti.me/note/parallel-vs-concurrent/
---

![](https://cdn-images-1.medium.com/max/1600/1*ylONk4ex9q6IK68C6USRBg.jpeg)

Note:
example: node requests & DB calls
---

## The JavaScript Engine
### and
## The JavaScript Runtime Environment
Note:
Can anyone describe these?
---
* **JavaScript Engine**:
interprets your JS code and turns it into runnable commands.
* **JavaScript Runtime Environemnt**:
supports your JavaScript by providing it with common objects and ways to communicate with the world outside your code
Note:

---
Which pieces belong to which parts?

![](https://camo.githubusercontent.com/bd3cc88e02a70dbd46694ef8ad2f0b5741725d7e/68747470733a2f2f63646e2d696d616765732d312e6d656469756d2e636f6d2f6d61782f3830302f312a4641394e47784e42362d76316f4932714745746c52512e706e67)
Note:
Walk step by step through the flow of the e-loop.  Define each part.
JS invokes an Environment API
---
How it all comes together:
```javascript
let cb1 = () => console.log('cb1');
console.log('hi');
setTimeout(cb1, 0);
console.log('bye');
```


![](https://camo.githubusercontent.com/df1ee9824df5f259718375500bdc2cbdca148934/68747470733a2f2f63646e2d696d616765732d312e6d656469756d2e636f6d2f6d61782f3830302f312a546f7a53726b6b39326c38686f3664384a7871465f772e676966)
---
# Asynchronicity
Note:
What does this mean?
What does synchronous mean?
---
## Asynchronicity in JS:
* Callbacks
* Promises, setTimeouts, ect.
Note:
The combination of callbacks and promises on top of the task queue and event loop are what give us asynchronicity in JS.

---
## What is a callback in JavaScript?
note: Lets go over a quick definition 
---

### **Callback:**
a function passed into another function as an argument <br> which is then invoked inside the second function to complete some kind of routine or action.
note:

lets look at an example

---

Synchronous:
```javascript
function log(number) {
    console.log(number);
}

function callAsap(callback, msg) {
    callback(msg);
}

callAsap(log, "Yay callbacks");
```

---

Also Synchronous:
```javascript
function log(number) {
    console.log(number);
}

function callAsapLoop(callback, msg, loops) {
    for(let i = 0; i < loops; i++) {
        callback(msg);
    }
}

callAsapLoop(log, "Yay callbacks", 100);

console.log("after loop")
```
---

Asynchronous:
```javascript
function log(msg) {
  console.log(msg);
}

function waitAndCall(callback, msg, waitTime) {
  setTimeout(() => callback(msg), waitTime);
}

waitAndCall(log, "After waiting 1000ms", 1000);
```
---

Also Asynchronous:
```javascript
function log(msg) {
  console.log(msg);
}

function waitAndCall(callback, msg, waitTime) {
  setTimeout(() => callback(msg), waitTime);
}

waitAndCall(log, "After waiting 1000ms", 1000);

console.log("end of file");
```
note: now that we understand Asynchronous
change 1000 ms to 0ms
---
## What is a promise in JavaScript?
---
### **Promise:**
an object that represents the eventual completion (or failure) of an asynchronous operation
Note:
Promises allow us to wait for asynchronous code and then execute other code upon completion.
---
Custom promise
```javascript
let quickPromise = new Promise( (resolve, reject) => {
    console.log("inside promise constructor");
    resolve("resolution argument");
});

quickPromise.then( arg => {
    console.log(".then invoked. Argument: " + arg);
});
```
---
Custom 1 second promise:
```javascript
let slowPromise = new Promise( (resolve, reject) => {
    console.log("inside promise constructor");
    setTimeout(() => resolve("resolution argument"), 1000);
});

slowPromise.then( arg => {
    console.log(".then invoked. Argument: " + arg);
});

console.log("After .then");
```
---
Goal: <br/>
Make an api call that uses
<br/>the result from previous api calls
```javascript
function makeSlowPromise(resArg) {
  return new Promise((resolve, reject) => {
    setTimeout(() => resolve(resArg), 1000);
  });
}

let fakeAPI = makeSlowPromise;

fakeAPI("res - 1").then(res1 => {
    console.log(res1);
    fakeAPI(res1 + " - 2").then(res2 => {
        console.log(res2);
        fakeAPI(res2 + " - 3").then(res3 => {
            console.log(res3);
        });
    });
});
```
---
With Promise chaining

```javascript
function makeSlowPromise(resArg) {
  return new Promise((resolve, reject) => {
    setTimeout(() => resolve(resArg), 1000);
  });
}

let fakeAPI = makeSlowPromise;

fakeAPI("res - 1").then(res1 => {
    console.log(res1);
    return fakeAPI(res1 + " - 2")
}).then(res2 => {
    console.log(res2);
    return fakeAPI(res2 + " - 3")
}).then(res3 => {
    console.log(res3);
});

```
---
# What is hoisting?
Note:
Ask for examples.
---
### Hoisting:
* Hoisting is JavaScript's default behavior of moving all _**declarations**_ to the top of the current scope (ie: current script or function).
Note:
What is a declaration?  Vs assignment/initialization?

---

Example:
```javascript
function doStuff() {
    console.log(a);
    
    var a = "now I exist";
    console.log(a);
}
```
---
## Primitives in JavaScript
Note:
What are they?
    not an object and has no methods
how are they different from objects?
pass by value vs pass by reference:
    pass by ref = pass the pointer
---
* ### string
* ### number
* ### boolean
* ### null
* ### undefined
* ### symbol (new in ECMAScript 2015)
note:
Have no properties
---
How can primitives have no properties?<br/>
What about `"string".length` and so on...
```javascript
String.prototype.returnMe = function() {
    return this;
}
 
a = "abc";
b = "abc".returnMe();
```
---
# Random Trivia
---
## Are there implicit return in JavaScript?
---
## Yes!
* Single line arrow functions
* Functions invoked with the _new_ keyword
* _async_ functions (implicitly return a promise)
---
## What are the 7 falsey values in javascript?
---
* false
* null
* undefined
* 0
* NaN
* ""
* document.all
---
## What is the difference between null and undefined?
---
## What is the value of this inside of a setTimeout function?
note:
```JavaScript
setTimeout(function () {
	console.log(this);
}, 500)
```
---
## What is the Value of this inside of a constructor function?
* Object is created before the constructor is run, When we invoke the keyword new, this becomes set to the instance of the new object.  The __proto__ of the new object is then set to the prototype of the constructor function.  __proto__ is just a pointer that JS is going to use to climb the prototype chain.
---
## Does javascript pass parameter by value or by reference?
* It depends on the datatype. Primitive types (string, number, etc.) are passed by value and objects are passed by reference. If you change a property of the passed object, the object will be affected.
---
# 10 minute break
---

# DOM Manipulation

---

## Is there any difference between window and document?

* Well, the window is the first thing that gets loaded into the browser. This window object has the majority of the properties like length, innerWidth, innerHeight, name, if it has been closed, its parents, and more.

* What about the document object then?
  * The document object is your html, aspx, php, or other document that will be loaded into the browser. The document actually gets loaded inside the window object and has properties available to it like title, URL, cookie, etc. What does this really mean? That means if you want to access a property for the window it is window.property, if it is document it is window.document.property which is also available in short as document.property.

---

## Do ```document.onload``` and ```window.onload``` fire at the same time?
* Window.onload
  * By default, it is fired when the entire page loads, including its content (images, css, scripts, etc.)
  * In some browsers it now takes over the role of document.onload and fires when the DOM is ready as well.
* Document.onload
  * It is called when the DOM is ready which can be prior to images and other external content is loaded.

---

## What are the different ways to get an element from DOM?
* getElementById
* getElementByClassName
* getElementsByTagName
* querySelector
* querySelectorAll

---

## What are the different ways to select elements by using css selectors?

Note:

* ID (#myID)
* Class (.myClass)
* Tag (div, p)
* Sibling (div+p, div~p)
* child (div>p)
* Descendant (div p)
* Universal (\*)
* Attribute (input[type="checkbox"])
* Pseudo (p:first-child)

---

## Can I use forEach or similar array methods on an HTMLCollection? How about a NodeList?
* An HTML collection can only contain element nodes ie. div, span, p etc.

* A nodeList collection can contain element nodes and other types of nodes.  In the DOM everything is a node and every node is an object, the name is a generic catch all.

* We cannot over an HTML Collection but we can over a NodeList

* QuerySelectorAll returns a nodeList and getElementsByTagName returns an HTMLCollection

---

## How do you implement getElementsByAttribute?

* document.all, cast it to an array.  Iterate over the array using for of loop and node.hasAttribute(‘href’).  Push nodes that do have the attribute to a result array.

```JavaScript
let b = document.all

let result = [];
for (let node of b) {
	if (node.hasAttribute('href')) {
		result.push(node)
    }
}
```

---

## How would you add a class to an element by query selector?

```JavaScript
var list;
list = document.querySelectorAll("li");
for (var i = 0; i < list.length; ++i) {
   list[i].classList.add('cf');
}
```

---

## How could I verify whether one element is child of another?

```JavaScript
function isDescendant(parent, child) {
     var node = child.parentNode;
     while (node != null) {
         if (node == parent) {
             return true;
         }
         node = node.parentNode;
     }
     return false;
}
```

---

## What is the best way to create a DOM element?

* `document.createElement(‘div’)` for one element

---

## What is createDocumentFragment and why might you use it?

* We can create a document fragment to append new elements onto it and we can style those elements as well with classnames or inline styles, then we can append them onto the document body all at once by appending the document fragment to avoid multiple repaints and reflows

```javascript
const list = ['foo', 'bar', 'baz'...], el, text;

for (let i = 0; i < list.length; i++) {
    el = document.createElement('li');
    text = document.createTextNode(list[i]);
    el.appendChild(text);
    document.body.appendChild(el);
}
```

---

## What is reflow? What causes reflow? How could you reduce reflow?

* Reflow is similar to repaint only when we have a reflow it’s even more critical to performance because it involves changes that affect the layout of a portion of the page (or the whole page). Reflow of an element causes the subsequent reflow of all child and ancestor elements as well as any elements following it in the DOM.  Essentially it means we’ve moved the element around on the page.

---

## What is repaint and when does this happen?

* A repaint occurs when changes are made to an elements skin that changes visibility, but do not affect its layout. Examples of this include outline, visibility, or background color.

---

## How could you make sure to run some javaScript when the DOM is ready, i.e. ```$(document).ready```?

```JavaScript
document.addEventListener("DOMContentLoaded", function() {
    // Your code to run since DOM is loaded and ready
});
```

---

## What is event bubbling?
* When an event happens on an element, it first runs the handlers on it, then on its parent, then all the way up on other ancestors.

* Let’s say we have 3 nested elements `FORM > DIV > P` with a handler on each of them:

* A click on the inner <p> first runs onclick:
  1.	On that <p\>.
  2.	Then on the outer <div\>.
  3.	Then on the outer <form\>.
  4.	And so on upwards till the document object.


* We can also go the other way with capturing where we click on a top level element and drill down on its descendants.  This is rarely used but if we did want to use it we can set the third argument to addEventListener to true.

```JavaScript
elem.addEventListener("click", e => alert(`Capturing: ${elem.tagName}`), true);
```

---

## What is the difference between ```event.target``` and ```event.currentTarget```?

* `target is` the element that triggered the event (e.g., the user clicked on)

*	`currentTarget` is the element that the event listener is attached to.

* `target = element that triggered event`; `currentTarget = element that listens to event`.

```html
<div id="1">1
  <div id="2">2</div>
</div>
```
* If we had an event listener on one but clicked on two the `target` would be two and the `currentTarget` would be one

---

## How could you destroy multiple list items with one click handler?

* We can actually leverage event bubbling. You can have only one event handler attached to the parent element of one hundred list items. In this case, you can attach the event handler to the `ul` tag. After you click on a list item (list item does not have an event), event will bubble and `ul` has a handler. That handler will be fired.

```html
<ul id="listToDestroy">
    <li><a href="#">first item</a></li>
    <li><a href="#">second item</a></li>
    <li><a href="#">third item</a></li>
    <li><a href="#">forth item</a></li>
    <li><a href="#">Fifth item</a></li>
</ul>
```
```JavaScript
document.getElementById('listToDestroy').addEventListener('click', function (e) {
    var elm = e.target.parentNode;
        elm.parentNode.removeChild(elm);
        e.preventDefault();
});
```

---

## How could you capture all clicks in a page?

* Put a click handler on the window

`window.onclick = function(e) { alert(e.target)};`

---

## How could you capture all the text in a web page?

`document.body.innerText`

---

# CSS

---

## What does float do?

* Float pushes an element to the sides of a page with text wrapped around it. you can create entire page or a smaller area by using float. if size of a floated element changes, text around it will re-flow to accommodate the changes. You can have float left, right, none or inherit.

* if you set, 'float: left;' for an image, it will move to the left until the margin, padding or border of another block-level element is reached. The normal flow will wrap around on the right side.

---

## How can you clear sides of a floating element?
* With the clear property

```CSS
div {
	clear: left;
        }
```

* The clear property can have one of the following values:
	* none - Allows floating elements on both sides. This is default
	* left - No floating elements allowed on the left side
	* right- No floating elements allowed on the right side
	* both - No floating elements allowed on either the left or the right side
	* inherit - The element inherits the clear value of its parent

---

## What are pseudo selectors?

`:hover, :nth-of-type, :visited, :focus, :link, :first, :child, :checked, :last-child, :target`

---

## What are the different types of positions in CSS?

* static: Default value. Elements render in order, as they appear in the document flow

* absolute:	The element is positioned relative to its first positioned (not static) ancestor element

* fixed:	The element is positioned relative to the browser window
relative: The element is positioned relative to its normal position, so "left:20px" adds 20 pixels to the element's LEFT position

* sticky: The element is positioned based on the user's scroll position. A sticky element toggles between relative and fixed, depending on the scroll position. It is positioned relative until a given offset position is met in the viewport - then it "sticks" in place (like position:fixed).

Note:
Not supported in IE/Edge 15 or earlier. Supported in Safari from version 6.1 with a -webkit- prefix.

---

## What are the differences between inline, block and inline-block?

* inline, elements do not break the flow. think of span it fits in the line. Important points about inline elements, margin/ padding will push other elements horizontally not vertically. Moreover, inline elements ignores height and width.

* block, breaks the flow and dont sits inline. they are usually container like div, section, ul and also text p, h1, etc.

* inline-block, will be similar to inline and will go with the flow of the page. Only differences is this this will take height and width.

---

## Are CSS properties case sensitive?
* By default "all CSS syntax is case-insensitive (...)" 

* There are exceptions, "(...) except for parts that are not under the control of CSS”[1]

* 2.1. element names are case-sensitive in HTML5 (?) and XML, but case-insensitive in HTML4.

* 2.2. identifiers (including element names, classes, and IDs in selectors) are case-sensitive. HTML attributes id and class, of font names, and of URIs lies outside the scope of the CSS specification.

---

# HTML

---

## How could you highlight text using only HTML?

```HTML
<mark>Text</mark>
```

---

## How could you reverse some text on the page using only HTML?

```HTML
<bdo dir="rtl">
This text will go right-to-left.
</bdo>
```

---

## What is a semantic HTML tag?

* Semantic tags are tags that describe what they are. e.g. - header, footer, marquee etc.  You should always favor semantic tags over generic divs for screen-readers and other accessibility reasons.

---

## What is an optional closing tag?
* Some tags such as <br\> and <a\> are self closing and therefor don't require closing tags

---

## Why do you need doctype at the beginning of your HTML document?

* The HTML syntax of HTML5 requires a DOCTYPE to be specified to ensure that the browser renders the page in standards mode vs Quirks Mode. The DOCTYPE has no other purpose and is therefore optional for XML. Documents with an XML media type are always handled in standards mode. [DOCTYPE]

* The DOCTYPE declaration is <!DOCTYPE html> and is case-insensitive in the HTML syntax. DOCTYPEs from earlier versions of HTML were longer because the HTML language was SGML-based and therefore required a reference to a DTD. With HTML5 this is no longer the case and the DOCTYPE is only needed to enable standards mode for documents written using the HTML syntax. Browsers already do this for <!DOCTYPE html>.


---

## When you zoom in on your browser and the page gets bigger, what exactly happens?

* Zooming as implemented in modern browsers consists of nothing more than “stretching up” pixels. That is, the width of the element is not changed from 128 to 256 pixels; instead the actual pixels are doubled in size. Formally, the element still has a width of 128 CSS pixels, even though it happens to take the space of 256 device pixels.

* In other words, zooming to 200% makes one CSS pixel grow to four times the size of one device pixels. (Two times the width, two times the height, yields four times in total).
---

## What does the ``` <details> ``` tag do?

---

```HTML
<details>
  <summary>Copyright 1999-2014.</summary>
  <p> - by Refsnes Data. All Rights Reserved.</p>
  <p>All content and graphics on this web site are the property of the company Refsnes Data.</p>
</details>
```
