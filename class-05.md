### Read: Class 05 - Thinking in React:

![React - Paradox Statement](https://miro.medium.com/max/3410/1*Dee4cg5Hzg7JME1A9tjZJQ.png)

## Thinking in React

### 1. How would you break a mock into a component heirarchy?

- Draw boxes around every component (and sub-component) in the mock and give them all names.
- Use single responsibility principle, that is, a component should ideally only do one thing
- Separate your UI into components, where each component matches one piece of your data model. finally pass the data between them using the props and state

### 2. What is the single responsibility principle and how does it apply to components?

A computer-programming principle that states that every module, class or function in a computer program should have responsibility over a single part of that program's functionality, and it should encapsulate that part. All of that module, class or function's services should be narrowly aligned with that responsibility.

### Example:

![Component Hierarchy](https://reactjs.org/static/eb8bda25806a89ebdc838813bdfa3601/6b2ea/thinking-in-react-components.png)

1. FilterableProductTable (orange): contains the entirety of the example
2. SearchBar (blue): receives all user input
3. ProductTable (green): displays & filter the data collection based on user input
4. ProductCategoryRow (turquoise): displays a heading for each category
5. ProductRow (red): displays a row for each product

---

### 3. What does it mean to build a ‘static’ version of your application?

It means to build a version of the app that takes your data model and renders the UI but, has no interactivity using props without using state.

### 4. Once you have a static application, what do you need to add?

make the UI interactive. and this can be done by using the state to trigger changes.

### 5. What are the three questions you can ask to determine if something is state?

- Is it passed in from a parent via props? If so, it probably
- Does it remain unchanged over time? If so, it probably
- Can you compute it based on any other state or props in your component?

if the answer of any of these questions: yes, so it's not state.

### 6. How can you identify where state needs to live?

- Identify every component that renders something based on that state.
- Find a common owner component (a single component above all the components that need the state in the hierarchy).
- Either the common owner or another component higher up in the hierarchy should own the state.
- If you can’t find a component where it makes sense to own the state, create a new component solely for holding the state and add it somewhere in the hierarchy above the common owner component.

![Component Life Cycle](https://www.wikitechy.com/tutorials/react/img/reactjs-images/ReactJS-components-life-cycle.png)

---

## Things I want to know more about

Go deeply into component Hierarchy, Paradox Statement and Component Life Cycle
Today the subject "Thinking in React" and all content is important and need to explore.
