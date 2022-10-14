# HTML
* Hypertext Markup Language
* Another markup language so that means it is just telling the computer what to do and not compiling it into machine code
* Very similar to xml (our .csproj files) but HTML is used to define the structure of our webpages
* Our browsers are essentially experts at reading this files and interpreting it to display something on the browser
* We are currently on version HTML 5

## HTML elements
* They are a basic graphical unit of something you want to display/structure on your web page
## HTML tags
* They are what you write in an HTML file to reference the HTML element you want to add
* Ex: I want to add an HTML paragraph element by typing ``<p></p>`` HTML tag
## Inline vs. Block elements
* Block elements will add a new line every time you create that element
* Inline element will not add a new line when you create that element
## Semantic tags
* Whole purpose of semantic tags is to express a clearly defined purpose of a certain section of your HTML file
* Unlike a div or span element that tells you absolutely nothing of what is going to be inside the contents
* Ex: table, article, form, etc.
## HTML attributes
* They are used to provide extra information that the tag can use
* Some changes the behavior or extends the functionality of the tag
* Ex: img tag using src attribute to find a specific image to display

# CSS
* Cascading Style Sheets
    * Cascading is in the name because the styling is determined by cascading down from one source to another source to another source and so on...
* A way to stop making your website looking like it came from the 90s

## CSS Terminologies/Anatomy
![alt text](https://github.com/220919-Reston-Java-React-AWS/reviews/blob/main/img/CSS%20Anatomy.png)

## CSS Selectors
* Before applying styles everywhere, we need a way to select specific or group of HTMl elements first so we give them their own type of look
* There are three basic fundamental selectors we should keep in mind:
1. Element selector - When you want to select multiple elements of the same tag
2. Class selector - When you want to select multiple elements of differing tag by using the class attribute
3. Id selector - When you want to select one elements using the id attribute

### Advance Selectors
1. Universal selector - will select everything denoted by using `*`
```CSS
* {
    color: red;
}
```
2. Attribute selector - will select a specific HTML attribute
```CSS
/* This will select every input element that has an attribute type with a value of number */
input[type='number'] {
    color: red;
}
```
3. Child selector - will select the nested/child elements
```CSS
/* Will select every child element that is inside of a div element */
div > * {
    color: red;
}

/* Will select a span element that is inside a paragraph and inside a div */
div > p > span {
    color: red;
}
```


## Different ways to include CSS
* Inline CSS
    * Applies CSS to a single element
    * It uses the style attribute
* Internal CSS
    * Applies CSS by using the style tag inside of a HTML doc
    * Used to apply multiple css to multiple elements
* External CSS
    * Creating an external .css file to apply css to multiple HTML docs (you can just apply it to one HTML but that kind of defeats the purpose of using an external css)
    * HTML doc must use the link tag to reference the external css
    * Used to apply multiple css to multiple elements in multiple HTML docs
        * So useful to create a universal theme of your website

## Box Model
* Great for us to move elements around the page to a specific location that we want
* From inner to outer:
    Content > Padding > Border > Margin
![alt text](https://github.com/220919-Reston-Java-React-AWS/reviews/blob/main/img/CSS%20Box.png)
* I would look into css flexbox to really help with positioning things in your website. Unfortunately, we don't have to cover it but it is really useful.
    * https://css-tricks.com/snippets/css/a-guide-to-flexbox

## CSS Specificity
* Key thing is the term "Specificity"
* This will determine what style we should apply to a particular element because sometimes some styling will collide with another
* General rule:
    * Inline CSS will have the highest priority
    * Id selector will have high priority
    * class selector will have second priority
    * element selector will have third priority

# Responsive Web Design (Optional but good thing to know)
* Making your elements not have rigid in size but changes its size based on the viewport
    * Viewport is just how big the window of the browser is (small for phones, big for computers)
* Useful to accomodate for every devices out there that might access your website
* We will leverage Bootstrap libraries for pre-made css files to implement this design
    * Click [here](https://getbootstrap.com/docs/5.1/getting-started/introduction/) for Bootstrap documentation

# HTML DOM
* Allows JavaScript to specifically pick certain elements in the HTML and change/manipulate them based on whatever function you want
* This is what makes JS a powerful tool to making your html page dynamically change based on whatever the user is doing
* The main idea is that JS uses objects and functions as its way to interact while HTML uses elements to interact. So a DOM was made so Javascript will know how to interact with HTML since they have different architecture on how things are done

# Events
* Events happen (usually) when the user interacts with the website in some shape or form.
* Ex: User clicking on a button, User pressing on keyboards, User using the mouse wheel, etc.
* For an HTML element to listen to a particular event, you give in an attribute that starts with "on..."
    * Ex: onclick, onmouseover, onkeydown, onkeyup, etc.
```HTML
<button onclick="someJSFunction()">Click me</button>
```
## Event Listeners
* Another way to add HTML elements to listen for events without giving it an attribute
* You use JS to add it instead
```JS
// Takes in 3 parameters
// first - the event it is listening to
// second - the function it executes if the event happens
// third - do you want it to have capturing behavior?
someElement.addEventListener("click", () => {/* Some behavior */}, true);
```

## Bubbling Event
* Where ever the event has started from (depending on what HTML element), it will bubble up and execute the parent element's event if there is one then it will execute the next parent element and so on and on...
## Capturing Event
* Opposite of Bubbling
* It will execute from the parent element down to the child element
![alt text](https://github.com/220919-Reston-Java-React-AWS/reviews/blob/main/img/Events.png)

# Classes
* As you know, templates for creating objects
* Didn't use to exist which made things weird and divided some communities in JS
    * Essentially some people say to never use it because it's inefficient or error prone
    * Some people say to use it because it makes looking at your code easier to read (you should see example of how JS used to implement class-like things using just functions (spoiler alert: it looks gross))
* Has most of the OOP pillars we discussed and implements them easily except abstraction

# Introduction to sending and receiving data in JS
## AJAX
* Asynchronous JS and XML
* Used to grab information only with XML type backend server hence the name
    * But they want ahead and updated the object to also include JSON to be relevant
## Fetch
* Similar to AJAX except less syntaxes or prepping needed to call on backend
* Main difference from AJAX is it uses promises to achieve asynchrnous operations
### Promises
* Represents either the completion or failure of an asynchronous operation
* Allows you to "setup" what to do after a completion of a promise and get its result and also account for a failure of a promise and what to do using "then()".

## Nice to know with JS
### Scopes
* The scope of a variable determines where it has access to
* Block
    * Cannot be access from outside {}
    ```JS
    {
        let x = 2;
    }
    //Anything outside cannot see that x variable
    ```
* Function scope
    * Each function you create is a new scope
    * Kinda like methods in C# in that variables created in the function only stays in that function
* Function scope
    * Can be access anywhere in JS
    * Var keyword that will give variable a global scope
    ```JS
    {
        var x = 2;
    }
    //Anything outside this block scope still has access to x because it is functional scope
    ```
* let keyword limits the scope of the variable depending on where it was declared
    * Mostly use "let" to try your best to avoid conflicting variable names