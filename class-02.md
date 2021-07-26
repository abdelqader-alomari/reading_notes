### Read: Class 02 - State and Props:

## React Component Life-Cycle

![React Component Life-Cycle](https://innovationm.co/wp-content/uploads/2018/05/React-Compnonent-Lifecycle-final.png)

### **what happens first, the ‘render’ or the ‘componentDidMount’?**

Based on the component life-cycle diagram the **the ‘render’ happens first**.

### **What is the very first thing to happen in the lifecycle of React?**

The first thing will happen is mounting => When an instance of a component is being created and inserted into the DOM it occurs during the mounting phase.

### **The order of lifecycle events happening:**

1. constructor
2. render
3. componentDidMount
4. React Updates
5. componentWillUnmount

### **componentDidMount:**

- This method is invoked immediately after a component is mounted. If you need to load anything using a network request or initialize the DOM, it should go here.

- `setState()` can be called here
- We can to connect to YouTube API and get videos when the components is rendered.

---

### **What types of things can you pass in the props?**

- Pass your counter component its initial count inside of the props.
- As example from video passing a title and a subtitle through the props
  and then the application knows if those props change at some point.
- So we can pass any data from parent to child component.

### **What is the big difference between props and state?**

- Props: pass into a component and handled outside of the component and must be
  updated outside of the component. and cannot change it inside the component

- State is handled inside of that component and you can update it inside
  the component. you can change it inside the component but need to re-render.

### **When do we re-render our application?**

when we change the state inside of our application it's going to re-render.

### **What are some examples of things that we could store in state?**

Store what they're updating that value to and what they're changing that value...
