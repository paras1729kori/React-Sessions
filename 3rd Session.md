# React Crash Course
## Recap
In last class, we learnt
* The traditional way of creating react app or getting a template for react apps is made by running create-react-app and then the app name
* useState is a combination of a variable and a function, it is used for changing the state of a variable when the react-app is rendered again
* Props are the coolest part of React Components which makes React code more reusable and helps adding more features to it
* Styling in react is similar to what we normally do, but while writing inline css remember to use camelCase style for writing the css
* Components modules are used to seperate different modules which makes the code more readable.

## Making a Search Bar Component
* Make a folder SearchBar (inside SearchBar.js and SearchBar.css)
* Import the css file
* Import SearchBar in App.js
```javascript
import React from 'react'
import './SearchBar.css'

const SearchBar = ()  => {
    return (
        <div>
            <input type='text'/>
        </div>
    )
}

export default SearchBar;
```
* When I put a value attr in this and give it a value 'saitama', it remains and does not
* So, I just wanted to point out that there is an attr we can use to get these values from the backend
* Because we are using React, we can make a var
```javascript
const searchValue
= "the seach value"

<input type="text"  value={searchValue} />
```
* Now, this is similar to what we did while making the last component

## onUpdate/onChange Event Listener
* Like the last time, we had a onClick attr which is used when a buttons gets clicked
* This time it is this function
* So, our goal is to make a search bar right, to be more precise a search bar where there are some predefined things
* For that too happen, the react should know what is being typed in the search bar
* That's why we use this onChnage event with the state hook
```javascript
import React, { useState } from 'react'
import './SearchBar.css'

const SearchBar = ()  => {
    const [searchValue, setSearchValue] = useState('the search value')

    const handleInputChange = (event) => {
        setSearchValue(event.target.value)
    }

    return (
        <div>
            <input type='text' value={searchValue} onChange={handleInputChange}/>
            {searchValue}
        </div>
    )
}

export default SearchBar;
```
* 
Now, there are many ways of handling inputs, but this is the most recommended one and used one

## Clear Button for Search Bar
* The goal is whenever the user clicks clear the bar should be cleared
* And we are using states so that shouldn't be much of a big deal
```javascript
// just think what can you do, it's a one line code
const handleClearClick = () => {
    setSearchValue('')
}

<button onClick={handleClearClick}>Clear</button>
```

## Conditinal Rendering
* It's just a fancy name, the thing we are concerned is that the button should come only when there is text inside the search bar
* Simply use logic and write the code
```javascript
const shouldDisplayButton = searchValue.length > 0

// this is short-circuiting 
// just think of it as if else condition or as a ternary operator
{shouldDisplayButton && <button onClick={handleClearClick}>Clear</button>}
```

## Rendering a list & Map Function
* The idea is to make a search bar is that when we write something in it, it should give us those results which matches it (Just a small thing which covers some imprtant concepts)
* Before this let's talk about map function
* So, what function does is, it puts the items of an array and map them in a different array
* If this is too complicated, think of it as looping over
```javascript
const products = [
    "tooth paste",
    "tooth brush",
    "mouth wash",
    "dental floss",
    "mouth gaurd"
]

console.log(products.map((product) => {
    return product.toUpperCase()
}))

<ul>
    {products.map((product) => {
        return <li>{product}</li>
    })}
</ul>
```
* Now, if you see the console, it is giving us an error
* So, whenver we use map, for each child to be different React wants every child to have a unique key
* Simply, put a key attr in li and value as {product}

## Filter Function
* Naam hi bata raha hai, what it does
```javascript
console.log(
    products.filter((product) => {
        return product.includes('tooth')
    })
)
```
```javascript
const filteredProducts = products.filter((product) => {
        return product.includes(searchValue)
})
// products => filteredProducts
```

## useEffect Hook
* This is used when we need to respond to different life cycle of the component
* Matlab performing some when the component is at a particular state
> Read Definition
```javascript
useEffect(() => {
    if(currentCount === 10 || currentCount > 10){
        setCurrentCount(0)
    }
}, [currentCount])
```

## Loader Thingy
* Remember the loading things we get when we go on a website, it's either an image or some text, or whatever.
* We'll see how do we do that, cause most of the times we won't be writing the data within the app but fetching it from an api
* Simply add a setTimeout function in a useEffect Hook, why inside a useEffect because whenever the user refreshers the page other components should not be disturbed
```javascript
// code written in App.js
// a state variable
const [productState, setProductState] = useState([])
useEffect(() => {
    setTimeout(() => {
        setProductState([
            "tooth brush",
            "tooth paste",
            "mouth wash",
            "mouth guard",
            "dental floss"
        ])
    }, 2000)
},[])

// then while passing the data in component
// we'll use teranry operator
{ productState.length > 0 ? <SearchBar list_item={productState} /> : <h1>Loading ...</h1>}
```

## useContext Hook
* Manier times there are many layers of components, like App > Com1 > Test1 && Test 2 && Com2 > Test3 && Test4
* And we don't wanna go on passing props from one layer to another
> * Add a MyContext.js file
```javascript
import { createContext } from 'react'

export const myContext = createContext(null)
```
* Import in App.js
```javascript
import { MyContext } from './MyContext'
// Wrap the body of with  <MyContext.Provider> tags
```
* Make a Test Component and add the code


## Children Props
* Example if we make a Button Component
* And import it in App.js
* This time instead of writing a self closing tag, we'll write the HTML way
```javascript
<Button>Btn1</Button>
<Button>Btn2</Button>
<Button>Btn3</Button>

import React from 'react'
const Button = (props) => {
    // console.log(props.children)

    return (
        <div>
            <button>{props.children}</button>
        </div>
    )
}
export default Button
```
* That's it

_I hope I have given you all a fair idea about what React is and what power it beholds_

*Happy Hacking ✌*