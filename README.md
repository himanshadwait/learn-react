# Table of Contents

- [Table of Contents](#table-of-contents)
  - [React ](#react-)
  - [Intro to JSX ](#intro-to-jsx-)
    - [What is JSX? ](#what-is-jsx-)
    - [JSX Elements ](#jsx-elements-)
    - [JSX Elements And Their Surroundings ](#jsx-elements-and-their-surroundings-)
    - [Attributes In JSX ](#attributes-in-jsx-)
    - [Nested JSX ](#nested-jsx-)
    - [JSX Outer Elements](#jsx-outer-elements)
    - [Rendering JSX](#rendering-jsx)
    - [Rendering JSX Explained](#rendering-jsx-explained)
    - [Passing a Variable to render()](#passing-a-variable-to-render)
    - [The Virtual DOM](#the-virtual-dom)
  - [Advanced JSX](#advanced-jsx)
    - [class vs className](#class-vs-classname)
    - [Self-Closing Tags](#self-closing-tags)
    - [JavaScript In JSX In JavaScript file](#javascript-in-jsx-in-javascript-file)
    - [Curly Braces in JSX](#curly-braces-in-jsx)
    - [Variables in JSX](#variables-in-jsx)
    - [Variable Attributes in JSX](#variable-attributes-in-jsx)
    - [Event Listeners in JSX](#event-listeners-in-jsx)
    - [JSX Conditionals](#jsx-conditionals)
      - [If Statements That Don't Work](#if-statements-that-dont-work)
      - [If Statements That Do Work](#if-statements-that-do-work)
      - [The Ternary Operator](#the-ternary-operator)
      - [\&\& operator](#-operator)

## React <a name="react"></a>

React.js is a JavaScript library developed by engineers at Facebook.

- React is fast. Apps made in React can handle complex updates and still feel quick and responsive.
- React is modular. Instead of writing large, dense files of code, you can write many smaller, reusable files. React’s modularity can be a beautiful solution to JavaScript’s maintainability problems.
- React is scalable. Large programs that display a lot of changing data are where React performs best.
- React is flexible. You can use React for interesting projects that have nothing to do with making a web app. People are still figuring out React’s potential. There’s room to explore.
- React is popular. While this reason has admittedly little to do with React’s quality, the truth is that understanding React will make you more employable.

## Intro to JSX <a name="jsx"></a>

Take a look at the following line of code:

`const h1 = <h1>Hello world</h1>;`
What kind of weird hybrid code is that? Is it JavaScript? HTML? Or something else?

It seems like it must be JavaScript since it starts with `const` and ends with `;`. If you tried to run that in an HTML file, it wouldn’t work.

However, the code also contains `<h1>Hello world</h1>`, which looks exactly like HTML. That part wouldn’t work if you tried to run it in a JavaScript file.

What’s going on?

Does this code belong in a JavaScript file, an HTML file, or somewhere else?

The answer is… a JavaScript file! Despite what it looks like, your code doesn’t actually contain any HTML at all.

The part that looks like HTML, `<h1>Hello world</h1>`, is something called **JSX**.

### What is JSX? <a name="jsxDef"></a>

JSX is a syntax extension for JavaScript. It was written to be used with React. JSX code looks a lot like HTML.

What does “syntax extension” mean?

In this case, it means that JSX is not valid JavaScript. Web browsers can’t read it!

If a JavaScript file contains JSX code, then that file will have to be compiled. This means that before the file reaches a web browser, a JSX compiler will translate any JSX into regular JavaScript.

Are there any browsers with a JSX compiler built in?

Unfortunately, there are no browsers (currently) with a JSX compiler built in. On our personal computers we will need to set up a way for our JSX code to compile when building react applications that use JSX.

### JSX Elements <a name="elements"></a>

A basic unit of JSX is called a JSX element.

Here’s an example of a JSX element:

`<h1>Hello world</h1>`
This JSX element looks exactly like HTML! The only noticeable difference is that you would find it in a JavaScript file, instead of in an HTML file

Is a JSX element the same thing as an HTML element?

A JSX element is not the same thing as an HTML element - a JSX element is a description of what we want to see on our page.

### JSX Elements And Their Surroundings <a name="elements-and-surroundings"></a>

JSX elements are treated as JavaScript expressions. They can go anywhere that JavaScript expressions can go. This means that a JSX element can be saved in a variable, passed to a function, stored in an object or array… you name it.

Here’s an example of a JSX element being saved in a variable:

`const navBar = <nav>I am a nav bar</nav>;`
Here’s an example of several JSX elements being stored in an object:

```
const myTeam = {
  center: <li>Benzo Walli</li>,
  powerForward: <li>Rasha Loa</li>,
  smallForward: <li>Tayshaun Dasmoto</li>,
  shootingGuard: <li>Colmar Cumberbatch</li>,
  pointGuard: <li>Femi Billon</li>
};
```

Do I have to use valid HTML tags when creating JSX elements?

When creating JSX elements, not components, we should be using valid HTML tags - that said, React uses some DOM properties/attributes differently than in HTML. Be sure to check the React documentation when adding HTML attributes to JSX elements to make sure that 1. the syntax is correct and 2. the attribute behavior is as expected.\

### Attributes In JSX <a name="attributes"></a>

JSX elements can have attributes, just like how HTML elements can.

A JSX attribute is written using HTML-like syntax: a name, followed by an equals sign, followed by a value. The value should be wrapped in quotes, like this:

`my-attribute-name="my-attribute-value"`
Here are some JSX elements with attributes:

```
<a href='http://www.example.com'>Welcome to the Web</a>;
const title = <h1 id='title'>Introduction to React.js: Part I</h1>;
```

A single JSX element can have many attributes, just like in HTML:

`const panda = <img src='images/panda.jpg' alt='panda' width='500px' height='500px'>;`

Can I create my own JSX element attributes?

We can create our own JSX element attributes! When we create our own JSX attributes we should not include whitespace in the attribute name, instead we should use either dashes or camelCase to separate multi-word attributes, or we can use our custom multi-word attribute name as a single word.

Example:

```
const myH1 =
  <h1
    my-custom-attribute="my-custom-attribute-value"
    myOtherCustomAttribute="my-other-custom-attribute-value"
    anothercustomattribute="another-custom-attribute-value"
  >
    Hello React
  </h1>


// All of the above attributes `my-custom-attribute`, `myOtherCustomAttribute`, and `anothercustomattribute` are valid JSX
// Attributes

```

### Nested JSX <a name="nested-jsx"></a>

You can nest JSX elements inside of other JSX elements, just like in HTML.

Here’s an example of a JSX `<h1> `element, nested inside of a JSX `<a>` element:

`<a href="https://www.example.com"><h1>Click me!</h1></a>`
To make this more readable, you can use HTML-style line breaks and indentation:

```
<a href="https://www.example.com">
  <h1>
    Click me!
  </h1>
</a>
```

If a JSX expression takes up more than one line, then you must wrap the multi-line JSX expression in parentheses. This looks strange at first, but you get used to it:

```
(
  <a href="https://www.example.com">
    <h1>
      Click me!
    </h1>
  </a>
)
```

Nested JSX expressions can be saved as variables, passed to functions, etc., just like non-nested JSX expressions can! Here’s an example of a nested JSX expression being saved as a variable:

```
 const theExample = (
   <a href="https://www.example.com">
     <h1>
       Click me!
     </h1>
   </a>
 );
```

Why do we need parentheses around multi-line JSX expressions?

We want to use parentheses around multi-line JSX expressions to make sure we are avoiding JavaScript’s automatic semicolon insertion which will add semicolons (based on rules given by the JavaScript specifications) to terminate statements when we don’t necessarily want/expect that behavior in a JSX expression.

Wrong usage

`let myVariable = <div><h1>&nbsp; Hello world!</h1></div>;`
Semicolon ";" inside "&nbsp;" breaks nesting, as it is not treated as part of JSX expression, but it is treated as basic js syntax.

Correct usage

`let myVariable = ( <div><h1>&nbsp; Hello world!</h1></div> );`
this way any semicolon between "(" and ")" is ignored by js interpreter.

### JSX Outer Elements

A JSX expression must have exactly one outermost element.

In other words, this code will work:

```
const paragraphs = (
  <div id="i-am-the-outermost-element">
    <p>I am a paragraph.</p>
    <p>I, too, am a paragraph.</p>
  </div>
);
```

But this code will not work:

```
const paragraphs = (
  <p>I am a paragraph.</p>
  <p>I, too, am a paragraph.</p>
);
```

The first opening tag and the final closing tag of a JSX expression must belong to the same JSX element!
It’s easy to forget about this rule and end up with errors that are tough to diagnose.
If you notice that a JSX expression has multiple outer elements, the solution is usually simple: wrap the JSX expression in a `<div>` element.

Can I wrap multi-line JSX expressions in an element other than a `<div>`?

JSX expressions can be wrapped in an element other than a `<div>` element to be sure that the first opening tag and final closing tag of a JSX expression belong to the same element.

This element can be an HTML element where the nesting is valid according to HTML5 specifications (see MDN documentation to check for permitted content in a specific element) or, this element can be custom components that have child components or other HTML elements nested inside.

You can also use the short syntax for this purpose.

```
<>
<p>Hello there</p>
<p>Have a nice day!</p>
</>
```

it’s on the official site of [React](https://legacy.reactjs.org/docs/fragments.html#short-syntax).

You can also use [Fragments](https://legacy.reactjs.org/docs/fragments.html#short-syntax).
Fragments let you group a list of children without adding extra nodes to the DOM.

```
render() {
  return (
    <React.Fragment>
      <ChildA />
      <ChildB />
      <ChildC />
    </React.Fragment>
  );
}
```

### Rendering JSX

To render a JSX expression means to make it appear on screen.

The following code will render a JSX expression:

```
const container = document.getElementById('app');
const root = createRoot(container);
root.render(<h1>Hello world</h1>);
```

The complete code is:

```
import React from 'react';
import { createRoot } from 'react-dom/client';

const container = document.getElementById('app');
const root = createRoot(container);
root.render(<h1>Hello world</h1>);
```

What’s the difference between React and ReactDOM?

React is a JavaScript library for building User Interfaces and ReactDOM is the JavaScript library that allows React to interact with the DOM.

### Rendering JSX Explained

Let’s examine the code that you just wrote in the last exercise.

```
const container = document.getElementById('app');
const root = createRoot(container);
root.render(<h1>Hello world</h1>);
```

Before we get started it is essential to understand that React relies on two things to render: `what content to render` and `where to place the content at`.

With that in mind, let’s look at the first line:

`const container = document.getElementById('app');`
This line:

- Uses the `document` object which represents our web page.
- Uses the `getElementById()` method of `document` to get the Element object representing the HTML element with the passed in id `(app)`.
- Stores the element in variable `container`.

In the next line:

`const root = createRoot(container);`
we use `createRoot()` from the `react-dom/client` library, which creates a React root from `container` and stores it in `root`. `root` can be used to render a JSX expression. This is the "where to place the content" part of React rendering.

Finally, the last line:

`root.render(<h1>Hello world</h1>)`
uses the `render()` method of `root` to render the content passed in as an argument. Here we pass an `<h1>` element, which displays Hello world. This is the "what content to render" part of React rendering.

Is the ReactDOM library built into the React library?

ReactDOM is not included in the generic React library. When we include the generic React library as a `<script>` tag in our HTML we will also have to include a `<script>` tag for the ReactDOM library if we want to use ReactDOM. We no longer use CDN links
to include React in our existing projects.

### Passing a Variable to render()

In the previous exercise, we saw how we can create a React root using `createRoot()` and use its `render()` method to render JSX.

The `render()` method’s argument doesn’t need to be JSX, but it should evaluate to a JSX expression. The argument could also be a variable, so long as that variable evaluates to a JSX expression.

In this example, we save a JSX expression as a variable named `toDoList`. We then pass `toDoList` as the argument of `render()`:

```
const toDoList = (
  <ol>
    <li>Learn React</li>
    <li>Become a Developer</li>
  </ol>
);

const container = document.getElementById('app');
const root = createRoot(container);
root.render(toDoList);
```

Why use a variable as the first argument in `ReactDOM.render()` instead of a JSX expression?

Readability! If we are trying to pass a multi-line JSX expression to `ReactDOM.render()` we may find our JSX code is difficult to read and understand, however, if our JSX expression is a single line, we may want to pass the expression (instead of a variable storing the expression) to `ReactDOM.render()`.

### The Virtual DOM

One special thing about a React root's `render()` method is that it only updates DOM elements that have changed.

That means that if you render the exact same thing twice in a row, the second render will do nothing:

`const hello = <h1>Hello world</h1>;`

// This will add "Hello world" to the screen:
`root.render(hello, document.getElementById('app'));`

// This won't do anything at all:
`root.render(hello, document.getElementById('app'));`
This is significant! Only updating the necessary DOM elements is a large part of what makes React so successful. This is accomplished using React’s virtual DOM.

## Advanced JSX

### class vs className

Grammar in JSX is mostly the same as in HTML, but there are subtle differences to watch out for. The most frequent of these involves the word `class`.

In HTML, it’s common to use `class` as an attribute name:

`<h1 class="big">Title</h1>`
In JSX, you can’t use the word `class`! You have to use `className` instead:

`<h1 className="big">Title</h1>`
This is because JSX gets translated into JavaScript, and `class` is a reserved word in JavaScript.

When JSX is rendered, JSX `className` attributes are automatically rendered as `class` attributes.

Are there any other HTML attributes that are reserved keywords in JavaScript that I wont be able to use in JSX?

In JSX, some HTML attributes will use camelCase and/or a different attribute name, but the two main attributes to be aware of (as we’ll use these most often and because their original HTML attribute name is a reserved JavaScript keyword) are:

- `class` - which will be `className` in JSX
- `for` - which will be `htmlFor` in JSX
  To read about more HTML attributes that use different names in JSX, check the React documentation for Tags and Attributes.

### Self-Closing Tags

Another common JSX error involves self-closing tags.

What’s a self-closing tag?

Most HTML elements use two tags: an opening tag `(<div>)`, and a closing tag `(</div>)`. However, some HTML elements such as `<img>` and `<input>` use only one tag. The tag that belongs to a single-tag element isn’t an opening tag or a closing tag; it’s a self-closing tag.

When you write a self-closing tag in HTML, it is optional to include a forward slash immediately before the final angle bracket:

```
// Fine in HTML with a slash:
<br />

// Also fine, without the slash:
<br>
```

But, in JSX, you have to include the slash. If you write a self-closing tag in JSX and forget the slash, you will raise an error:

```
// Fine in JSX:
<br />

// NOT FINE AT ALL in JSX:
<br>
```

Can I use self-closing tag syntax for any HTML elements I use in JSX?

You can! HTML elements we write in JSX can be self-closing as long as we use the forward-slash with right angle bracket to close the element tag.

For example:

`<div className="myDiv" />`
Now when would this be useful? Making a self-closing element is useful when said element has no children, this should be the only time we use self-closing syntax for HTML elements that are normally not self-closing.

### JavaScript In JSX In JavaScript file

So far, we’ve focused on writing JSX expressions. It’s similar to writing bits of HTML, but inside of a JavaScript file.

Now, we’re going to add something new: regular JavaScript, written inside of a JSX expression, written inside of a JavaScript file.

Why would we want to put JavaScript in our JSX?

We want to use JavaScript in our JSX to render logic!

When we inject JS into JSX we can make this process of rendering logic (based on things like data, events, and data changing over time) more seamless by putting our markup, the HTML part of JSX, that is based on our logic, the JS part of JSX, together in the same file.

```
import React from 'react';
import { createRoot } from 'react-dom/client';

const container = document.getElementById('app');
const root = createRoot(container);
// Write code here:
root.render(<h1>2 + 3</h1>);
```

### Curly Braces in JSX

The last piece of code didn’t behave as one might expect. Instead of adding 2 and 3, it printed out "2 + 3" as a string of text. Why?

This happened because 2 + 3 is located in between `<h1>` and `</h1>` tags.

Any code in between the tags of a JSX element will be read as JSX, not as regular JavaScript! JSX doesn’t add numbers—it reads them as text, just like HTML.

You need a way to write code that says, “Even though I am located in between JSX tags, treat me like ordinary JavaScript and not like JSX.”

You can do this by wrapping your code in **curly braces**.

Everything inside of the curly braces will be treated as regular JavaScript.

```
import React from 'react';
import { createRoot } from 'react-dom/client';

const container = document.getElementById('app');
const root = createRoot(container);
// Write code here:
root.render(<h1>{2 + 3}</h1>);
```

Am I always going to use curly braces to write JavaScript inside of JSX?

Yes! If we want any expression to be treated as JavaScript inside of a JSX element we need to wrap it in curly braces. Even when we assign a JavaScript expression to a variable and want to use that variable inside JSX, the variable name needs to be wrapped in curly braces.

Example:

```
app.js:

import React from 'react';
import ReactDOM from 'react-dom';

let myVar = 'hello!';

const myJsxElement = <h1>myVar value is {myVar}</h1>;
// `myVar` without curly braces will render as `myVar`
// in the browser, while `{myVar}` will render as `hello!` in the browser

ReactDOM.render(
        myJsxElement,
        document.getElementById('app')
)
```

We can see a JSX expression that displays the first twenty digits of pi.

Study the expression and notice the following:

The code is written in a JavaScript file. By default, it will all be treated as regular JavaScript.

Find `<div>` on line 5. From there, up through `</div>`, the code will be treated as JSX.

Find `Math`. From there, up through `(20)`, the code will be treated as regular JavaScript again.

The curly braces themselves won’t be treated as JSX or as JavaScript. They are markers that signal the beginning and end of a JavaScript injection into JSX, similar to the quotation marks that signal the boundaries of a string.

```
import React from 'react';
import ReactDOM from 'react-dom';

const pi = (
  <div>
    <h1>
      PI, YALL!
    </h1>
    <p>
      {Math.PI.toFixed(20)}
    </p>
  </div>
);

ReactDOM.render(
	pi,
	document.getElementById('app')
);
```

### Variables in JSX

When you inject JavaScript into JSX, that JavaScript is part of the same environment as the rest of the JavaScript in your file.

That means that you can access variables while inside of a JSX expression, even if those variables were declared outside of the JSX code block.

```
// Declare a variable:
const name = 'Gerdo';

// Access your variable inside of a JSX expression:
const greeting = <p>Hello, {name}!</p>;
```

Can I inject other programming languages besides JavaScript into JSX?

No, we cannot inject other programming languages other than JavaScript into JSX. We can only inject vaild JavaScript expression into JSX by wrapping the JS expression in curly braces.

When should I assign a variable to a JavaScript expression that I want to use in a JSX expression?

The use of variables to store JavaScript expressions will largely be based on preference. However, we will usually want to use variables assigned to our JS expressions when our JS code would otherwise be hard to read/follow before using our JS expression inside of our JSX.
For example:

```
import React from 'react';
import ReactDOM from 'react-dom';

ReactDOM.render(<h1>two + two = {2 + 2}</h1>, document.getElementById('app'));
// Here, the JavaScript expression `2+2` is easy to read
// and understand what's going on in the code
```

vs.

```
import React from 'react';
import ReactDOM from 'react-dom';

const myFunc  = (a, b) => {
  //do some logic or calculations with parameters here
}


ReactDOM.render(<h1>{myFunc(3,4)}</h1>, document.getElementById('app'));
// Here, we assign a function to the variable `myFunc` then call the myFunc
// fuction from inside our JSX - this is especially useful if the logic
// inside myFunc would be difficult to read and understand from inside a JSX expression
```

### Variable Attributes in JSX

When writing JSX, it’s common to use variables to set attributes.

Here’s an example of how that might work:

```
// Use a variable to set the `height` and `width` attributes:

const sideLength = "200px";

const panda = (
  <img
    src="images/panda.jpg"
    alt="panda"
    height={sideLength}
    width={sideLength} />
);
```

Notice how in this example, the `<img />‘s` attributes each get their own line. This can make your code more readable if you have a lot of attributes for one element.

Object properties are also often used to set attributes:

```
const pics = {
  panda: "http://bit.ly/1Tqltv5",
  owl: "http://bit.ly/1XGtkM3",
  owlCat: "http://bit.ly/1Upbczi"
};

const panda = (
  <img
    src={pics.panda}
    alt="Lazy Panda" />
);

const owl = (
  <img
    src={pics.owl}
    alt="Unimpressed Owl" />
);

const owlCat = (
  <img
    src={pics.owlCat}
    alt="Ghastly Abomination" />
);
```

### Event Listeners in JSX

JSX elements can have event listeners, just like HTML elements can. Programming in React means constantly working with event listeners.

You create an event listener by giving a JSX element a special attribute. Here’s an example:

`<img onClick={clickAlert} />`
An event listener attribute's name should be something like `onClick` or `onMouseOver`: the word `on` plus the type of event that you're listening for. Look through the [common components list in React docs](https://react.dev/reference/react-dom/components/common#) to browse supported event names.

An event listener attribute's value should be a function. The above example would only work if `clickAlert` were a valid function that had been defined elsewhere:

```
function clickAlert() {
  alert('You clicked this image!');
}

<img onClick={clickAlert} />
```

Note that in HTML, event listener names are written in all lowercase, such as `onclick` or `onmouseover`. In JSX, event listener names are written in camelCase, such as `onClick` or `onMouseOver`.

Remember, since attributes are a part of JSX expressions, you will need to inject JavaScript in order to use `clickAlert`.

Why don’t we set the event listener attribute value to a function call?

If we set the event listener attribute value to a function call, the function will get called automatically on the page load (when our JSX element renders to the browser) instead of listening for the event and then calling the function.

For example:

```
import React from 'react';
import ReactDOM from 'react-dom';

function switchHeading() {
  console.log('switchHeading was called!');
}

const heading = (
  <h1 onClick={switchHeading}>Click Me!</h1>

  // onClick will listen for the click event, then will
  // call switchHeading. When that occurrs we will see
  // 'switchHeading was called!' logged to the console

  // if <h1 onClick={switchHeading()}>Click Me!</h1>
  // is used instead, and we set onClick to a function call,
  // we will see 'switchHeading was called!' logged to the
  // console immediately when our JSX renders and not on the click event
)

ReactDOM.render(heading, document.getElementById('app'));
```

### JSX Conditionals

#### If Statements That Don't Work

Great work! you've learned how to use curly braces to inject JavaScript into a JSX expression!

Here’s a rule that you need to know: you can not inject an if statement into a JSX expression.

This code will break:

```
(
  <h1>
    {
      if (purchase.complete) {
        'Thank you for placing an order!'
      }
    }
  </h1>
)
```

What if you want a JSX expression to render but only under certain circumstances? You can’t inject an if statement. What can you do?

You have lots of options. let's explore some simple ways to write conditionals (expressions that are only executed under certain conditions) in JSX.

#### If Statements That Do Work

How can you write a conditional if you can't inject an if statement into JSX?

One option is to write an if statement and not inject it into JSX.

Look at the following code. Follow the if statement.

This works because the words if and else are not injected in between JSX tags. The if statement is on the outside, and no JavaScript injection is necessary.

This is a common way to express conditionals in JSX.

```
import React from 'react';
import { createRoot } from 'react-dom/client';

const container = document.getElementById('app');
const root = createRoot(container);
let message;

if (user.age >= drinkingAge) {
  message = (
    <h1>
      Hey, check out this alcoholic beverage!
    </h1>
  );
} else {
  message = (
    <h1>
      Hey, check out these earrings I got at Claire's!
    </h1>
  );
}

root.render(message);
```

Is there a way to conditionally show or hide an element?

When using a conditional to render an element, we can return null for a condition to make sure an element does not render based on the condition.

For example:

```
import React from 'react';
import ReactDOM from 'react-dom';

function showOrHide () {
  let myHideObj = {
    hide: false
  }

  if (myHideObj.hide === false) {
    let innerElement = (
      <h1>Not hidden!</h1>
    )
    return innerElement;
    // when myHideObj.hide property is set to false the if statement
    // will return innerElement and will render the element

  } else {
    return null;
    // when myHideObj.hide property is set to true we can return null
    // to make sure no element is rendered based on our condition
  }
}

const myElement = (
  <div>{showOrHide()}</div>
)

ReactDOM.render(myElement, document.getElementById('app'));
```

#### The Ternary Operator

There’s a more compact way to write conditionals in JSX: the ternary operator.

The ternary operator works the same way in React as it does in regular JavaScript. However, it shows up in React surprisingly often.

Recall how it works: you write `x ? y : z`, where x, y, and z are all JavaScript expressions. When your code is executed, x is evaluated as either "truthy" or "falsy". If x is truthy, then the entire ternary operator returns y. If x is falsy, then the entire ternary operator returns z.

Here’s how you might use the ternary operator in a JSX expression:

```
const headline = (
  <h1>
    { age >= drinkingAge ? 'Buy Drink' : 'Do Teen Stuff' }
  </h1>
);
```

In the above example, if age is greater than or equal to drinkingAge, then headline will equal `<h1>Buy Drink</h1>`. Otherwise, headline will equal `<h1>Do Teen Stuff</h1>`.

Why can I use a ternary operator inside a JSX expression but not an if statement?

We can use a ternary operator, also known as a conditional operator, inside a JSX expression because it will always evaluate to a value, where as an `if/else/else if` statement is not only not an expression (it’s a statement and will execute a statement based on the value of an expression), but will also not evaluate to a value.

In other words, we cannot use a statement where a value (or expression) is expected and for this reason, we cannot use statements, including the conditional `if/else/else if` statements, inside a JSX expression.

#### && operator

We’re going to cover one final way of writing conditionals in React: the `&&` operator.

Like the ternary operator, `&&` is not React-specific, but it shows up in React very often.

`&&` works best for conditionals that will sometimes do an action but other times do nothing at all.

Here’s an example:

```
const tasty = (
  <ul>
    <li>Applesauce</li>
    { !baby && <li>Pizza</li> }
    { age > 15 && <li>Brussels Sprouts</li> }
    { age > 20 && <li>Oysters</li> }
    { age > 25 && <li>Grappa</li> }
  </ul>
);
```

If the expression on the left of the `&&` evaluates as true, then the JSX on the right of the `&&` will be rendered. If the first expression is false, however, then the JSX to the right of the `&&` will be ignored and not rendered.

When should I use an `if` statement, a ternary operator, or the `&&` operator?

We should decide to use either an `if` statement, ternary operator, or the `&&` operator based on what is most concise while still maintaining readability.

Tips to help decide on which conditional statement or operator to use:

- the `&&` and ternary operators are more concise, choose either of these when possible
- choose the `&&` over a ternary when you want an action to occur (or not) based on a single condition
- choose an `if/else/else if` statement when you need to extrapolate logic to make it easier to read and understand
