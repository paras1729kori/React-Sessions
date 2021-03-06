# React Crash Course
## Recap
In last class, we learnt
* What is React ? --- A front-end framework
* What is DOM & similarly what is React-DOM ? --- The interface that let's JS talk to HTML
* Babel & JSX --- JSX is html with additional powers, and Babel is a transpiler that converts JSX to pure JS
* Components -- Nothing but a way for code reusability

<br>

# 2nd Session
## Create React App Template
* Now that we have a fair idea about what exactly react is all about
* We can now start learning the concepts or more of the different things react gives us to make our work more intereseting
* So, let's create our first react app "The Traditional Way"
* Simply, create a folder named whatever you like ('dsc-react' ig for me)
* Now, as you can see there are many different thing here but remember "Kaam se kaam rakho aur aage badho"
* So, don't focus on any other stuff
    * Just see that there is an index.html file like we had
    * And an App.js that is connected to it the same we connected pur js file in last lecture
* Let's run it
    * cd into your project folder
    * And run npm start
    * Voila !!!

## Building the same Count Button
* Now as I explained y'all earlier that we use components to make code more reusable, etc things
* Let's now create the same counter button components using react taht we made using normal JS earlier in the course
```javascript
import React from 'react'

const Component_Name = () => {
    const currentCount = 0
    // change it to let
    const handleClick = () => {
        currentCount++
        console.log(currentCount)
    }

    return (
        <div>
            <button onClick = {handleClick}>Increment By 1</button>
            <h1>{currentCount}</h1>
        </div>
    )
}

export default Component_Name;
```
* Why did this happen, it's because this only makes the React.DOM change itself and not the React.
* So, we use something called as useState, now I know this is a very big topic and sometimes people are skeptical about and get confused in this part, but don't worry I got you
* useState is a hook, Hooks are very important topics in React, and I'll be introducing y'all with 3 of those hooks, the 3 which are used the most (useState, useEffect, useContext)
* We'll see what useEffect, useContext are in the coming lecture, lets focus on useState for now.
```javascript
import React, { useState } from 'react'

const Component_Name = () => {
    // console.log(useState(0))
    const [currentCount, setCurrentCount] = useState(0)
    // 0 is a default value
    const handleClick = () => {
       currentCount++
       setCurrentCount(currentCount)
       // setCurrentCount(currentCount+1)
    }

    return (
        <div>
            <button onClick = {handleClick}>Increment By 1</button>
            <h1>{currentCount}</h1>
        </div>
    )
}

export default Component_Name;
```
* Now remember, what I said the most important part of using components is .... code reusability
* Simply add one more component in App.js and you are done writing your second button
* Now, lets take this one more step further, what is we want one of them to increment by 1 and another by 5, what do we do then any suggestions....
* We use something known as PROPS

## Props
* Pass incrementBy = {} props in each component.
* And change code acc.

## Props vs States
* Props are variables that are static, once passed they won't change again
* Whereas on the other hand , States are variables that change every time the react-dom changes i.e the page changes.

## Styling and Style Props
* In react we can do styling in 2 ways
    * The inline styling
    * And the external file styling
* The only different thing in React is that the CSS attributes are changed or written acc. to the JS text style i.e CamelCase style
* And for using external CSS simply add a css/scss file and import it in the JS component
```javascript
const btnStyle = {
    background:"blue",
    borderRadius: "8px"
}
// pass this as a style attr in button tag
```
* What if we want differen colors for each button ?
* Simplay make a buttonColor prop, give it a value and pass them in the btnStyle
> Comments in react are same as that in JS i.e /* */

## Component Modules
* Now most of the times in real-life situations, there are many components in a single page app
* So the developers make a component module, for that specific component

<br>

# KEYTAKEAWAYS
* The conventional way of creating react app or getting a template for react apps is made by running create-react-app and then the app name
* useState is a combination of a variable and a function, it is used for changing the state of a variable when the react-app is rendered again
* Props are the coolest part of React Components which makes React code more reusable and helps adding more features to it
* Styling in react is similar to what we normally do, but while writing inline css remember to use camelCase style for writing the css
* Components modules are used to seperate different modules which makes the code more readable