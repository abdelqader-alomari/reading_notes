### Read: Class 01 - Introduction to React and Components

## What is a Component?

- A component is a modular, portable, replaceable, and reusable set of well-defined functionality that encapsulates its implementation and exporting it as a higher-level interface.

- A component is a software object, intended to interact with other components, encapsulating certain functionality or a set of functionalities. It has an obviously defined interface and conforms to a recommended behavior common to all components within an architecture.

- A software component can be defined as a unit of composition with a contractually specified interface and explicit context dependencies only. That is, a software component can be independent and is subject to composition by third parties.

- #### A component can have three different views:

1. object-oriented view (viewed as a set of one or more cooperating classes)
2. conventional view (viewed as a functional element that integrates the processing logic)
3. and process-related view.(the system is building from existing components from a library)

## Characteristics of Components:

- Reusability − Components can be reused in different situations in different applications

- Replaceable − Components may be freely substituted with other similar components.

- Not context specific − Components can operate in different environments and contexts.

- Extensible − A component can be extended from existing components to provide new behavior.

- Encapsulated − component depicts the interfaces, which allow to use its functionality

- Independent − Components are designed to have minimal dependencies on other components.

## the advantages of using component based architecture:

- **Ease of deployment** − easy to replace existing versions without affect other components.

- **Reduced cost** − components allows you to spread the cost of development and maintenance.

- **Ease of development** − Components implement well-known interfaces to provide defined
  functionality, allowing development without impacting other parts of the system.

- **Reusable** − The use of reusable components means that they can be used to spread the
  development and maintenance cost across several applications or systems.

- **Modification** of technical complexity through using component container and its services.

- **Reliability** − The overall system reliability increases since the reliability of each
  individual component enhances the reliability of the whole system via reuse.

- **System maintenance and evolution** − Easy to change and update the implementation without
  affecting the rest of the system.

- **Independent** − Independency and flexible connectivity of components. Independent
  development of components by different group in parallel. Productivity for the software development and future software development.

---

## props stands for:

\*\*properties that used for passing data from one component to another used in React.

## How are props used in React?

1. define an attribute and its value(data)
   `<ChildComponent someAttribute={value} anotherAttribute={value}/>`
2. pass it to child component(s) by using Props.
   `const ChildComponent = (props) => {return <p>I'm the 1st child!</p>};`
3. Render the Props Data. Props returns back an object we access it by dot(.) notation..
   `const ChildComponent = (props) => {return <p>{props.text}</p>};`

## The flow of props

**Props can only be passed to components in one-way (parent to child)**
