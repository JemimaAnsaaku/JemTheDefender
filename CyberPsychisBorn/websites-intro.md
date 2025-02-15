# How websites work
By the end of the room I will understand how websites are created and i will learn basic security measures

## Websites

When we visit specific websites, our browsers (like safari or google) makes a request to a web server asking for information about the page i am visiting. the server will respond with data that our browsers use to show us the page. 

web server - dedicated computer somewhere else in the world that handles our requests

browser request gets transferred to the internet - request sent to server from server then the data response sent from server back through internet to the browser. 

there are two major components that make up a website:

1. front end (client side) - the way your browser renders a website

2. back end (server-side) - a server that processes your request and returns a response

there are many other processes involved in a browser making a request to a web server, but for now we just need to understand that you make a request to a web server and it responds with data the browser uses to render information to you.

## HTML 

websites are made using:

html - skeleton of the website- headers paragrapghs images

css - font, colour, layouts, some visual effects like pop ups

javascript - interactivity and functionality - dynamic content, animations, API requests, user interactions 


HTML is the language websites are written in. elements (also known as tags) are the building blocks of html pages and tells the browser how to display content. the code snippet shows a simple html document, the structure which is the same for every website 

```
<!DOCTYPE html>
```

This defines that the page is a html5 document  it helps with standardisation across different browswers and tells the browser to use HTML5 to interpret the page 

```
<html>
  <head>
    <title> page title </title>
  </head>
  <body>
    <h1> example headings </h1>
    <p> example paragraph </p>
  </body>
</html>
```

This element is the root element of the HTML page - all other elements come after this point 

```
<head>
  <title> page title </title>
</head>
```

this element contains information about the page - such as page title 

```
<body>
  <h1> example headings </h1>
  <p> example paragraph </p>
</body>
```

this element defines the HTML documesnt's body; ONLY content inside of the body is shown in the browser

```
<h1> example heading </h1>
```
this element is used within the body and defines a large heading 

```
<p> example paragraph </p>
```

this element defines a paragraph 

There are many other elements (tags) used for different purposes. for example, there are tags for buttons (<button>), images (<img>), lists and much more 

tags (elements) can contain attributes such as the class attribute when used to style an element for example 

```
<p class="bold-text">
```

or the src attribute which is used on images to specify the location of an image

```
<img src="img address">
```
an element can have multiple attributes each with iits own purppose e.g., <p attribute1="value1" attribute2="value2">.

elements can also have an id attribute <p id="example">), which is unique to the element. unlike the class attribute, where multiple elements can use the same class, an element must have different id's to identify them uniquely. element id's are used for styling and to identify it by javascript. 

You can view the HTML of any website by right-clicking and selecting "View Page Source" (Chrome) / "Show Page Source" (Safari).

## Javascript 

javascript (JS) is one of the most popular coding languages in the world and allows pages to become interactive. HTML is used to create website structure and content while javascript is used to control the functionality of web pages. without javascript, a page would not have interactive elements and would always be static. JS can dynamically update a page in real time, giving functionality to change of a button when a particular event on a page occurs (such as when a user clicks a button) or to display movinf animations.

Javascript is added within the page source code and can be either loaded within <script> tags or can be included remotely with src attribute

```
<script src="/location/of/javascript_file>
  </script>
```

the following javascript code finds a html element on the page with the id of "demo" and changes the elements contents to "hack the planet"

```
document.getElementById(d"demo").innerHTML = "Hack the Planet"
```

HTML elements can also have events such as "onclick" or "onhover" that execute javascript when the event occurs. The following code changes the text of the element with the demo id to button clicked. 


Events are actions that happen on a web page, like:

Clicking a button (onclick)

Hovering over something (onmouseover / onhover)

Typing in a text box (oninput)

A function in JavaScript is like a recipe or a set of instructions that you can tell the browser to follow whenever something happens. You "call" or "run" a function when you want it to do something.

Think of a function like this:

i (the user) want a sandwich.
i tell the chef (JavaScript) to make a sandwich for me.

the chef (function) follows my instructions (ingredients) and makes the sandwich (action) for me.

the function is the recipe: i can use it over and over again!

```
<!-- 1. HTML - The Structure -->
<p id="message">Hello!</p>
<button id="myButton">Click Me!</button>

<!-- 2. JavaScript - The Action -->
<script>
    document.getElementById("myButton").onclick = function() {
        document.getElementById("message").innerHTML = "You clicked the button!";
    };
</script>
```

```
<p id="message">Hello!</p>
<button id="myButton">Click Me!</button>
```

### HTML PART:

This is the structure.

<p id="message">Hello!</p> → A paragraph that says Hello!.

<button id="myButton">Click Me!</button> → A button that says Click Me!.

### JavaScript Part (What happens when you click the button):

```
document.getElementById("myButton").onclick = function() {
    document.getElementById("message").innerHTML = "You clicked the button!";
};
```
document.getElementById("myButton"): This finds the button by its id (myButton). its basically saying hey i want to work with mybutton

.onclick = function() {...}: his part sets up the function. It says: "Whenever the button is clicked, do something.". in this scenario 

```
function() {
    document.getElementById("message").innerHTML = "You clicked the button!";
}
```
is the function - and its job is to change the text in the button remember when clicked 

### What Happens When You Click the Button?

When you click the button, the JavaScript function runs.

The function will change the text in the paragraph from "Hello!" to "You clicked the button!".

The function is triggered by the click.

## Sensitive data exposure 

sensitive data exposure occurs when a website does not properly protect or remove sensitive clear-text information to the end user, usually found in a sites front end source code. 

we now know that websires are build using many html elements - all of which we can see simply by "viewing the page source". a website developer may have forgotten to remove login credentials, hidden links to private parts of the website or other sensitive data shown in the html or javascript.

sensitive information can be potentially leveraged to further an attackers access within different parts of a web application. for example, there could be html comments with temporary login credentials and if you viewed the page's source code and found this, i could use the credentials to login elsewhere on the application or worse, used to access oother backend components of the site.

whenever accessing a web application for security issues, one of the first thing to do is review if there have been any exposed login credentials or hidden links 

```
<!-- TODO: remove test credentials admin:password123 -->
```

## HTML Injection

HTML injection is a vulnerability that occurs when an unfiltered user input message is displayed on the page. If a websire fails to sanitise user input (filter any malicious texr that a user inputs into the site) and that input is used on the page, the attacker can inject html code into a vulnerable website

Think of a Website Like a Restaurant

### Imagine you go to a restaurant and order a burger. You tell the waiter:

🗣 "I'd like a burger, please."

The waiter writes it down and gives it to the chef, who makes your burger exactly as you ordered. Everything is fine ✅.

### What If Someone Tries to Trick the Chef?


Now, imagine a hacker comes in and instead of ordering a normal burger, they say:
🗣 "I'd like a burger, and also fire in the kitchen!"

If the waiter blindly repeats everything to the chef without checking, the chef might literally set the kitchen on fire 🔥 because they followed instructions exactly as written.

This is what HTML Injection does to websites!

### How This Relates to Websites

A website often asks users to enter information, like:

Comments on a blog

A username in a login form

A message in a contact form

A safe website checks and filters what users type to make sure it’s just normal text (like ordering a simple burger).

A badly coded website takes whatever the user types and blindly inserts it into the page, without checking if it's safe.

### Real Example of HTML Injection

Let’s say a website has a comment box:

🚨 Normal User Comment

```
hello, nice article!
```

the website displays it like 

```
<p>Hello, nice article!</p>
```
All good. The website shows the text exactly as written.

🚨 Hacker Comment (HTML Injection)

```
<b>You have been hacked!</b>
```
If the website doesn't check for bad input, it inserts this directly into the page:

```
<p><b>You have been hacked!</b></p>
```

🔥 Now, instead of displaying <b>You have been hacked!</b> as text, the browser renders it as HTML, making the text bold on the page!

So the website now looks different than it should because the hacker injected HTML.

### 🚨 Even Worse: Injecting JavaScript!

Hackers can take this further by injecting JavaScript.

For example, if a hacker types:

```
<script>alert("You have been hacked!");</script>
```

if the website does not sanitize input, it puts this directly into the page:

```
<p><script>alert("You have been hacked!");</script></p>
```

### <a> tag

The <a> tag in HTML is used to create hyperlinks (clickable links) that let users navigate to other pages, websites, or even different sections of the same page.

```
<a href="https://example.com">Click here</a>
```
<a> → The anchor tag (creates a link).

🔹 href="URL" → The hyperlink reference, which tells the browser where to go.

🔹 Between <a> and </a> → The text that becomes clickable.

## How Do Websites Prevent This?

To stop HTML Injection, websites must:

Filter and clean user input → Convert <script> into plain text so it doesn’t run.

Escape special characters → Change < to &lt; and > to &gt; so they show as text instead of running as code.

Use safe functions in JavaScript → Always use .textContent instead of .innerHTML to insert user input.

# General syntax rules 

## HTML BASICS

1. HTML Tags (Elements)
HTML uses tags to define structure. A tag is a command that tells the browser how to interpret the content. Every HTML element has an opening tag and a closing tag (except for self-closing elements). Opening tags define the start of the element; closing tags define the end. They always come in pairs: <tag></tag>. The content sits between the opening and closing tags.

Example:

<p>This is a paragraph</p>
In the above example, <p> is the opening tag and </p> is the closing tag. The text ‘This is a paragraph’ is the content inside the tag.

Why do we need both opening and closing tags? HTML tags are used to mark where content starts and ends. A pair of opening and closing tags keeps things organized. Without a closing tag, the browser wouldn’t know where the element ends, which could mess up the layout.

## 2. HTML Attributes
HTML attributes provide additional information about an element. Unlike tags, which wrap around content, attributes are added within the opening tag to modify its behavior or appearance.

Example: <a href="https://example.com">Click Here</a>

Here, the <a> tag creates a link, and the href attribute specifies the URL the link goes to. Notice: The href attribute is inside the opening <a> tag, not in a separate tag.

Why are attributes inside the opening tag? Attributes are not separate elements; they modify the behavior of the element itself. So, attributes are placed within the opening tag so they can be interpreted in relation to the element.

Best Practice: Attributes should always be enclosed in quotes. Without quotes, the browser might misinterpret them.

## 3. Self-Closing Tags
Self-closing tags don’t need a closing tag because they don’t contain any content. These tags automatically end after their opening tag. Common examples: <img>, <input>, <br>.

Example: <img src="image.jpg" alt="An image" /> <br />

These are self-closing tags.

Why do self-closing tags not need closing tags? These tags do not contain content between an opening and closing tag, so they don't need an explicit closing tag. Think of them like a single operation. You tell the browser "insert an image" or "break the line", and that’s all.

## 4. Comments in HTML
Comments are non-visible text used for explanations and notes in the code. They are ignored by the browser and do not affect the webpage’s layout or appearance.

Example:

<!-- This is a comment, it won’t show up on the page 😩-->
Why use comments? Comments help developers understand the code. It can explain the purpose of a section of code or remind developers of important notes. It's good practice to comment your code to make it easier for others (or yourself) to understand later.

# JAVASCRIPT BASICS

## 1. Variables
Variables are used to store data. In JavaScript, variables are created with let, const, or var.

Example: let name = "John";

Variables allow us to store values so they can be reused later. You can change the value of a variable, which makes your code more flexible.

Why use variables? Variables store values that you want to reuse. Instead of hardcoding a value repeatedly in different places, you store it in a variable and reference it.

## 2. Functions
Functions are reusable blocks of code that perform a specific task. They are declared using the function keyword.

Example: function greet() { console.log("Hello!"); } greet(); // Calling the function

Functions help keep code organized. You define the function once and call it whenever needed. This makes code easier to maintain and reduces repetition.

Why use functions? Functions help organize code into manageable sections. Instead of repeating similar code, you write it once as a function and call it wherever needed.

## 3. Events
JavaScript can listen for events such as clicks, mouse hovers, or key presses and react to them. Events are often used to trigger JavaScript code when an action is performed.

Example (onclick event): <button onclick="alert('Button clicked!')">Click Me!</button>

In this example, when the button is clicked, the JavaScript alert() function will run.

Why use events? Events make your page interactive. By responding to user actions, you can dynamically change the content or appearance of the page.

## 4. Conditionals
Conditionals (if, else, else if) allow you to execute different code depending on a condition.

Example: if (age >= 18) { console.log("Adult"); } else { console.log("Underage"); }

Conditionals let you control the flow of your code. They allow you to check if certain conditions are true or false and perform actions accordingly.

Why use conditionals? Conditionals are useful when you want to make decisions in your code. For example, check if a user is logged in, or if a product is in stock.

## 5. Loops
Loops repeat a block of code multiple times, saving you from writing repetitive code.

Example: for (let i = 0; i < 5; i++) { console.log(i); // Outputs 0, 1, 2, 3, 4 }

Loops are essential when you need to perform the same operation multiple times.

Why use loops? Loops reduce redundancy in your code. Instead of manually repeating code, loops handle repetitive tasks automatically.

## 6. Arrays
Arrays are used to store lists of values.

Example: let colors = ["red", "blue", "green"]; console.log(colors[0]); // Outputs "red"

Arrays allow you to group multiple values under a single variable, making data management simpler.

Why use arrays? Arrays help manage multiple values. For instance, if you need to store a list of users, colors, or items, arrays let you group and access them easily.

## 7. Objects
Objects store multiple values in key-value pairs, similar to how a dictionary works.

Example: let person = { name: "Alice", age: 25 }; console.log(person.name); // Outputs "Alice"

Objects are useful for storing related data. In the example above, we store a person’s name and age in a single object.

Why use objects? Objects allow you to organize related data into one place, making it easier to access and manipulate.

## INTERACTIONS BETWEEN HTML & JS

1. Accessing HTML Elements in JS
JavaScript can interact with HTML elements by their id or class attributes.

Example (access by id):

<p id="demo">Hello</p> <script> document.getElementById("demo").innerHTML = "Goodbye"; </script>
The JavaScript function getElementById() finds the element with the specified id and can modify its content, such as changing the inner HTML.

Why is this useful? This allows you to update content dynamically. For example, you might want to change a message when the user clicks a button.

- we are simply just referring to it with javascript yet
- 
2. Events and JS Interaction
You can attach JavaScript code to HTML events like clicks, key presses, etc.

Example (onclick event): <button onclick="alert('Button clicked!')">Click Me!</button>

When the button is clicked, JavaScript runs the alert() function, showing a popup with the message.

Why use events in JS? Events let you trigger actions based on user input or interaction. It’s how you add interactivity to web pages.

3. Modifying HTML with JS
JavaScript can change the content of HTML elements dynamically using properties like innerHTML or textContent.

Example:

<p id="message">Old Text</p> <script> document.getElementById("message").innerHTML = "New Text"; </script>
In this example, JavaScript changes the content inside the paragraph tag with id message from "Old Text" to "New Text".

Why modify HTML with JS? This is key for creating interactive and dynamic pages. For example, if a user submits a form, JavaScript could change the page’s content without needing to reload it.

4. Creating New Elements with JS
JavaScript can create new HTML elements and insert them into the document.

Example:

<script> let newPara = document.createElement("p"); newPara.innerHTML = "This is a new paragraph!"; document.body.appendChild(newPara); </script>
This example creates a new <p> element with some text and appends it to the body of the document.

Why create new elements? You can dynamically add content to a page, such as new comments, posts, or messages, without refreshing the page.

