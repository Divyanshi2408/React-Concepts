# React Lifecycle Methods

React lifecycle methods allow developers to hook into different stages of a component’s life and perform specific actions. These methods are only available in **class components**. 

Lifecycle methods are divided into three main phases:

1. **Mounting**: When the component is being created and inserted into the DOM.
2. **Updating**: When the component is being re-rendered due to changes in props or state.
3. **Unmounting**: When the component is being removed from the DOM.

---

## **1. Mounting**

These methods are called when a component is initialized and added to the DOM.

| **Method**           | **Description**                                                                                     |
|-----------------------|-----------------------------------------------------------------------------------------------------|
| `constructor()`       | Called before the component is mounted. Used for initializing state and binding methods.            |
| `static getDerivedStateFromProps(props, state)` | Allows state to be updated based on props. Rarely used.                              |
| `render()`            | Returns the JSX to be rendered in the DOM.                                                         |
| `componentDidMount()` | Invoked after the component has been mounted. Useful for making API calls or interacting with the DOM.|

---

## **2. Updating**

These methods are called when a component is re-rendered due to changes in state or props.

| **Method**                          | **Description**                                                                                     |
|-------------------------------------|-----------------------------------------------------------------------------------------------------|
| `static getDerivedStateFromProps()` | Invoked before rendering. Updates state based on changes in props.                                 |
| `shouldComponentUpdate(nextProps, nextState)` | Determines whether the component should re-render. Used for optimization.                      |
| `render()`                          | Re-renders the JSX based on the new state or props.                                                 |
| `getSnapshotBeforeUpdate(prevProps, prevState)` | Captures some information from the DOM before it is updated.                                    |
| `componentDidUpdate(prevProps, prevState, snapshot)` | Invoked after the update has been committed. Ideal for making network requests.               |

---

## **3. Unmounting**

This method is called when a component is removed from the DOM.

| **Method**           | **Description**                                                                                     |
|-----------------------|-----------------------------------------------------------------------------------------------------|
| `componentWillUnmount()` | Invoked just before a component is unmounted and destroyed. Useful for cleanup (e.g., removing timers, cancelling API calls). |

---

## **Deprecated Methods**

Some lifecycle methods have been deprecated in recent React versions:

| **Method**               | **Reason for Deprecation**                                                                       |
|--------------------------|-------------------------------------------------------------------------------------------------|
| `componentWillMount()`   | Replaced with the `constructor` or `componentDidMount`.                                         |
| `componentWillReceiveProps()` | Replaced with `getDerivedStateFromProps`.                                                  |
| `componentWillUpdate()`  | Replaced with `getDerivedStateFromProps` and `getSnapshotBeforeUpdate`.                         |

---

## **Conclusion**

Understanding React lifecycle methods is crucial when working with **class components**. While **functional components** use hooks like `useEffect` to handle similar behaviors, lifecycle methods are still essential for maintaining older React codebases.
