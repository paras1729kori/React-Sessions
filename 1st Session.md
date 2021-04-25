# React Crash Course

## Introduction
* What is React ?
* Pre requisite -- JS, Some basic functions like Map, Filter and ForEach
* So, first we'll see how to make react apps w/o using the more traditional way of making them

<br>

# 1st Session
## How to make a simple react app ?
* Pre requisite -- HTML, CSS, JS
* Whatever you do, it'll always start with a basic .htm file
* So, let's build your first react components ( A Counter Button), think of it as a "Hello, World" program for react doing it the traditional way first

> Continue with Code

## What is DOM ?
* It has a self explanatory name (Document Object Model)
* Think of DOM as a connector
* Think of it as a layer b/w the the HTML and JS
* It can access everything you have in your HTML page

> Continue with code and make a increment btn using normal JS
```javascript
const incrementBtn = document.getElementById('increment-btn')
const counstDisplay = document.getElementById('count-display')

let currentCount = 0
incrementBtn.addEventListerner("click", () => {
    counter++;
    countDisplay.innerHTML = currentCounter;
})
```

## React VS React-DOM
* Now, let's use React to make these things more easy and less repetitive
> * Add the two script tags
> * And make the div id=root
* React generates HTML code for us, that's why we don't write HTML, but we do end up writing something like HTML which is better known as JSX (Javascript XML)
* Think of React-DOM as an interpreter for React
* React-DOM renders everything that is written in React
>Continue with code
```html
<!-- index.htm file -->
<div class="root"></div>
<script src="index.js"></script>
```
```javascript
// Console these
console.log(React)
console.log(ReactDOM)
```

```javascript
// Snippet 1
const reactContentRoot = document.getElementById('root')
ReactDOM.render("hello world", reactContentRoot)

// Snippet 2
const reactContentRoot = document.getElementById('root')
const myFirstElemet = React.createElement('li', null, 'item 1')
ReactDOM.render(myFirstElemet, reactContentRoot)
```

## Babel & JSX
* None in actual html file
* Explain what is JSX.
    * JSX is nothing but modified HTML, in which we can write JS too. (To put it into layman terms)
* And how JSX is read by Babel
    * So, Babel is a tool that transpiles the JSX we write in our pages
> * Continue with code and add the babel code for using JSX<br>
> * Change the type of the script tag to text/babel

<br>

##### if you guys are running into an error, when running the JSX code.
##### Try running the html file in a server
##### If it is still not running. leave it not that important

<br>

## JSX Interpolation
* Before moving on to Components in React, let's see how do we interpolate things in React i.e. how to use variables (for the aasan bhasha mein people)
> Continue with code
```javascript
const listitem = 'Saitama';
const myJSX = (
    <ul>
        <li>item 1</li>
        <li>item 2</li>
        <li>{listitem.toUpperCase()}</li>
    </ul>
)
```
* There are many differences b/w JSX and HTML, they may look similar but they ain't similar

## React Componenets
* Components are nothing code that reduces lot of our time.
* The main use of making components is code reusablity
* That's it nothing else
* index.js is nothing but a component
* 2 types of components
    * Functional Component
    * Class Component
* We'll be only using functional components
```javascript
const reactContentRoot = document.getElementById('root')

const App = () => {
    const listitem = 'Saitama';
    return (
        <ul>
            <li>item 1</li>
            <li>item 2</li>
            <li>{listitem.toUpperCase()}</li>
        </ul>
    )
}

ReactDOM.render(<App />, reactContentRoot)
```

<br>

# KEY TAKEAWAYS
* What is React ? --- A front-end framework
* What is DOM & similarly what is React-DOM ? --- The interface that let's JS talk to HTML
* Babel & JSX --- JSX is html with additional powers, and Babel is a transpiler that converts JSX to pure JS.
* Components -- Nothing but a way for code reusability.