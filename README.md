# Fundamental of React.js
This is a practical introduction to the fundamentals of React.js with JavaScript and the basics of the DOM API.

## FAQ
### 1 .When to use a Class Component over a Function Component?
If the component needs state or lifecycle methods then use class component otherwise use function component. However, from React 16.8 with the addition of Hooks, you could use state , lifecycle methods and other features that were only available in class component right in your function component.

### 2. What is state in React?
State of a component is an object that holds some information that may change over the lifetime of the component. We should always try to make our state as simple as possible and minimize the number of stateful components.

Let's create an user component with message state,
```
class User extends React.Component {
  constructor(props) {
    super(props)

    this.state = {
      message: 'Welcome to React world'
    }
  }

  render() {
    return (
      <div>
        <h1>{this.state.message}</h1>
      </div>
    )
  }
}
```  
### 3. What is the difference between HTML and React event handling?

  a. In HTML, the event name should be in lowercase:
```
  <button onclick='activateLasers()'>
```  
  Whereas in React it follows camelCase convention:
```
  <button onClick={activateLasers}>
```  
  b. In HTML, you can return false to prevent default behavior:
```
  <a href='#' onclick='console.log("The link was clicked."); return false;' />
``` 
  Whereas in React you must call preventDefault() explicitly:
```
  function handleClick(event) {
    event.preventDefault()
    console.log('The link was clicked.')
  }
```  
  c. In HTML, you need to invoke the function by ``` appending () ``` Whereas in react you should not ```append ()``` with the function name. (refer "activateLasers" function in the first point for example)

### 4. What/ How Virtual DOM works?

### 5. What is the difference between Shadow DOM and Virtual DOM?
The Shadow DOM is a browser technology designed primarily for scoping variables and CSS in web components. The Virtual DOM is a concept implemented by libraries in JavaScript on top of browser APIs.

### 6. What are the different phases of component lifecycle?
The component lifecycle has three distinct lifecycle phases:

  a. Mounting: The component is ready to mount in the browser DOM. This phase covers initialization from``` constructor(), getDerivedStateFromProps(), render(), and componentDidMount()``` lifecycle methods.

  b. Updating: In this phase, the component get updated in two ways, sending the new props and updating the state either from ```setState() or forceUpdate()```. This phase covers ```getDerivedStateFromProps(), shouldComponentUpdate(), render(), getSnapshotBeforeUpdate() and componentDidUpdate() ``` lifecycle methods.

  c. Unmounting: In this last phase, the component is not needed and get unmounted from the browser DOM. This phase includes componentWillUnmount() lifecycle method.

It's worth mentioning that React internally has a concept of phases when applying changes to the DOM. They are separated as follows

  a. Render The component will render without any side-effects. This applies for Pure components and in this phase, React can pause, abort, or restart the render.

  b. Pre-commit Before the component actually applies the changes to the DOM, there is a moment that allows React to read from the DOM through the getSnapshotBeforeUpdate().

  c. Commit React works with the DOM and executes the final lifecycles respectively ```componentDidMount()``` for mounting, ```componentDidUpdate()``` for updating, and ```componentWillUnmount()``` for unmounting.

### 7. What are fragments?
It's common pattern in React which is used for a component to return multiple elements. Fragments let you group a list of children without adding extra nodes to the DOM.
```
  render() {
    return (
      <React.Fragment>
        <ChildA />
        <ChildB />
        <ChildC />
      </React.Fragment>
    )
  }
```  
There is also a shorter syntax, but it's not supported in many tools:
```
  render() {
    return (
      <>
        <ChildA />
        <ChildB />
        <ChildC />
      </>
    )
  }
 ``` 
### 8. What are stateless components?
If the behaviour is independent of its state then it can be a stateless component. You can use either a function or a class for creating stateless components. But unless you need to use a lifecycle hook in your components, you should go for function components. There are a lot of benefits if you decide to use function components here; they are easy to write, understand, and test, a little faster, and you can avoid the this keyword altogether.

### 9. What are stateful components?
If the behaviour of a component is dependent on the state of the component then it can be termed as stateful component. These stateful components are always class components and have a state that gets initialized in the constructor.
```
  class App extends Component {
    constructor(props) {
      super(props)
      this.state = { count: 0 }
    }

    render() {
      // ...
    }
  }
  ```
React 16.8 Update:

Hooks let you use state and other React features without writing classes.

The Equivalent Functional Component
```
 import React, {useState} from 'react';
 const App = (props) => {
   const [count, setCount] = useState(0);

   return (
     // JSX
   )
 }
 ```
 ### 10. What are the advantages of React?

  a. Increases the application's performance with Virtual DOM.
  b. JSX makes code easy to read and write.
  c. It renders both on client and server side (SSR).
  d. Easy to integrate with frameworks (Angular, Backbone) since it is only a view library.
  e. Easy to write unit and integration tests with tools such as Jest.
  
### 11. What is the benefit of Virtual DOM?
Each time you make a change in the code, DOM will be completely updated and rewritten. This is an expensive operation and consumes lots of time. In this point,  Virtual DOM in React provides a solution:
1. React first creates an exact copy of the DOM
2. Then React figures out which part is new and only updates that specific part in the Virtual DOM
3. Finally, React copies only the new parts of the Virtual DOM to the actual DOM, rather than completely rewriting it.

### 12.  what is this JSX?
JSX (JavaScript XML) is a syntax extension to JavaScript used by React. JSX is basically used to write HTML tags inside JavaScript. That is HTML tags are rendered directly inside JavaScript. JSX simplifies React and makes it easier to read.
