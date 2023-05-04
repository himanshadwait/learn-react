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

## React <a name="react"></a>

React.js is a JavaScript library developed by engineers at Facebook.
React is fast. Apps made in React can handle complex updates and still feel quick and responsive.
React is modular. Instead of writing large, dense files of code, you can write many smaller, reusable files. React’s modularity can be a beautiful solution to JavaScript’s maintainability problems.
React is scalable. Large programs that display a lot of changing data are where React performs best.
React is flexible. You can use React for interesting projects that have nothing to do with making a web app. People are still figuring out React’s potential. There’s room to explore.
React is popular. While this reason has admittedly little to do with React’s quality, the truth is that understanding React will make you more employable.

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

#### What is JSX? <a name="jsxDef"></a>

JSX is a syntax extension for JavaScript. It was written to be used with React. JSX code looks a lot like HTML.

What does “syntax extension” mean?

In this case, it means that JSX is not valid JavaScript. Web browsers can’t read it!

If a JavaScript file contains JSX code, then that file will have to be compiled. This means that before the file reaches a web browser, a JSX compiler will translate any JSX into regular JavaScript.

Are there any browsers with a JSX compiler built in?

Unfortunately, there are no browsers (currently) with a JSX compiler built in. On our personal computers we will need to set up a way for our JSX code to compile when building react applications that use JSX.

#### JSX Elements <a name="elements"></a>

A basic unit of JSX is called a JSX element.

Here’s an example of a JSX element:

`<h1>Hello world</h1>`
This JSX element looks exactly like HTML! The only noticeable difference is that you would find it in a JavaScript file, instead of in an HTML file

Is a JSX element the same thing as an HTML element?

A JSX element is not the same thing as an HTML element - a JSX element is a description of what we want to see on our page.

#### JSX Elements And Their Surroundings <a name="elements-and-surroundings"></a>

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

#### Attributes In JSX <a name="attributes"></a>

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

#### Nested JSX <a name="nested-jsx"></a>

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

#### JSX Outer Elements

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

#### Rendering JSX

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

#### Rendering JSX Explained
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

* Uses the `document` object which represents our web page.
* Uses the `getElementById()` method of `document` to get the Element object representing the HTML element with the passed in id ```(app)```.
* Stores the element in variable `container`.

In the next line:

`const root = createRoot(container);`
we use `createRoot()` from the `react-dom/client` library, which creates a React root from `container` and stores it in `root`. `root` can be used to render a JSX expression. This is the "where to place the content" part of React rendering.

Finally, the last line:

`root.render(<h1>Hello world</h1>)`
uses the `render()` method of `root` to render the content passed in as an argument. Here we pass an `<h1>` element, which displays Hello world. This is the "what content to render" part of React rendering.