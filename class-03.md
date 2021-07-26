### Read: Class 03 - Passing Functions as Props:

## lists and keys

![Lists and Keys](https://i.ytimg.com/vi/Jh47pOXwGq0/maxresdefault.jpg)

### **What does .map() return?**

it returns a new array with element passed through it (same or modified one)

### **If I want to loop through an array and display each value in JSX, how do I do that in React?**

1.  loop through the numbers array using the JavaScript map()
2.  assign the resulting array of elements to variable
3.  include the entire listItems array inside a <> element, and render it to the DOM

example from source:

`function NumberList(props) { const numbers = props.numbers; const listItems = numbers.map((number) => <li>{number}</li> ); return ( <ul>{listItems}</ul> ); }`

`const numbers = [1, 2, 3, 4, 5]; ReactDOM.render( <NumberList numbers={numbers} />, document.getElementById('root') );`

### **Each list item needs a unique _key_.**

### **What is the purpose of a key?**

Keys help React identify which items have changed, are added, or are removed. Keys should be given to the elements inside the array to give the elements a stable identity.

---

## The Spread Operator

![The Spread Operator](https://i.morioh.com/2019/11/19/580be7d831c1.jpg)

### **What is the spread operator?**

InJavaScript, spread syntax refers to the use of an ellipsis of three dots (…) to expand an iterable object into the list of arguments.

### **List 4 things that the spread operator can do.**

1. Copying and array
2. Concatenating or combining arrays
3. Using Math functions
4. Using an array as arguments
5. Adding an item to a list
6. Adding a state in React
7. Combining objects
8. Converting NodeList to an array

### **Give an example of using the spread operator to combine two arrays.**

`const array1 = [`a`,`b`,`c`] const array2 = [`d`,`e`,`f`] const outArray = [...array1,...array2] console.log(...outArray) // a b c d e f`

### **Give an example of using the spread operator to add a new item to an array.**

`const arr = ['a', 'b', 'c', 'd', 'e', 'f'] const outArray2 = [...arr, 'g', 'h', 'i'] console.log(outArray2) // ["a", "b", "c", "d", "e", "f", "g", "h", "i"] ... also I can add elements at start of an array`

### **Give an example of using the spread operator to combine two objects into one.**

example from source:

`const objectOne = {hello: "🤪"} const objectTwo = {world: "🐻"} const objectThree = {...objectOne, ...objectTwo, laugh: "😂"} console.log(objectThree) // Object { hello: "🤪", world: "🐻", laugh: "😂" } const objectFour = {...objectOne, ...objectTwo, laugh: () => {console.log("😂".repeat(5))}} objectFour.laugh() // 😂😂😂😂😂`

---

### **what is the first step that the developer does to pass functions between components?**

![Pass function between components](https://res.cloudinary.com/practicaldev/image/fetch/s--yg_ujrdW--/c_limit%2Cf_auto%2Cfl_progressive%2Cq_auto%2Cw_880/https://dev-to-uploads.s3.amazonaws.com/i/jbhsy030y0ocjvw7ipry.png)

make an object and create a method (function) so we can map or loop through and can access its value by props, and can use state.

### **In your own words, what does the increment function do?**

this is a function used to update (increase) the value whenever called... usually use counter increased by clicking

### **How can you pass a method from a parent component into a child component?**

we can access it by dot notation one by one or looping... then pass it from parent to child by props.

### **How does the child component invoke a method that was passed to it from a parent component?**

Answer that I found by search in the internet: Create a boolean variable in the state in the parent class. Update this when you want to call a function. Create a prop variable and assign the boolean variable. From the child component access that variable using props and execute the method you want by having an if condition.

---

## Things I want to know more about

I am excited to learn more about this topics and learn by practice.
