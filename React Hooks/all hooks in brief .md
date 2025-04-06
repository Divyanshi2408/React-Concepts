## 1. What is the useState hook in React and how does it work?
The useState hook is used to declare and manage state variables in functional components. It allows you to store a value and update it when needed, triggering a re-render of the component.

Syntax:
```
const [state, setState] = useState(initialValue);
```
---

## 2. What is the useEffect hook and when would you use it?
The useEffect hook is used to manage side effects in functional components. Side effects are operations that affect something outside the scope of the component, such as:

- Fetching data from an API
- Setting up subscriptions
- Manually changing the DOM
- Starting/stopping timers
Syntax:
```
useEffect(() => {
  // Side effect logic here

  return () => {
    // Cleanup logic (optional)
  };
}, [dependencies]);
```
The dependency array determines when the effect runs:
- []: Runs once on mount
- [state]: Runs when state changes
- No array: Runs on every render

---

## 3. What is the useContext hook and how is it useful?
The useContext hook is used to access context values in functional components. It allows you to share state or data globally across components without having to pass props manually through every level of the component tree (called "prop drilling").

**Create a context:**
```
const MyContext = React.createContext();
```
**Provide a value using the Provider:**
```
<MyContext.Provider value={someValue}>
  <ChildComponent />
</MyContext.Provider>
```
**Consume it in any component:**
```
const value = useContext(MyContext);
```
It’s especially useful for themes, authentication, or any global state.

---
## 4. What is the useRef hook and what are its use cases?
The useRef Hook allows you to persist values between renders.It can be used to store a mutable value that does not cause a re-render when updated.

Main use cases:

**Accessing DOM elements:**
```
const inputRef = useRef();
<input ref={inputRef} />
inputRef.current.focus(); // Focus input field
```
**Storing mutable values (like timers, previous state, etc.) without causing re-renders:**
```
const countRef = useRef(0);
countRef.current += 1;
```
So yes, it's used to "refer" to something – usually DOM nodes or persistent values.

## 5. What is the useMemo hook and why would you use it?
The useMemo hook is used for memoization – it caches the result of a computation and only recalculates it when its dependencies change. This helps in optimizing performance by avoiding unnecessary recalculations.

Use when:
- You have an expensive function (like filtering, sorting, or calculations).
- The result is used in rendering.

Syntax:
```
const memoizedValue = useMemo(() => computeExpensiveValue(a, b), [a, b]);
```
If a and b haven’t changed, useMemo returns the cached value.

---

## 6. What is the useCallback hook and how is it different from useMemo?
The useCallback hook is used to memoize a function, so that it’s not recreated on every render unless its dependencies change.

This is helpful when you pass functions as props to child components — it prevents unnecessary re-renders and improves performance.

Syntax:
```
const memoizedFn = useCallback(() => {
  // Your function logic
}, [dependencies]);
```
Difference from useMemo:
- useMemo returns a memoized value.
- useCallback returns a memoized function.

**You can think of this:**
```
useCallback(fn, deps) === useMemo(() => fn, deps)
```
---

## 7. What is the useReducer hook and when would you use it instead of useState?
The useReducer hook is used for managing complex state logic in functional components, especially when:

- State depends on previous state.
- Multiple related state updates need to be grouped.
- The state logic is too complex for useState.

It works similarly to how Redux reducers work — with a reducer function and a dispatch method.

Syntax:
```
const [state, dispatch] = useReducer(reducer, initialState);

function reducer(state, action) {
  switch (action.type) {
    case "increment":
      return { count: state.count + 1 };
    case "decrement":
      return { count: state.count - 1 };
    default:
      return state;
  }
}
```
- When to use useReducer instead of useState:
- When you have multiple related state values.
- When state transitions are complex.
- When you want to move state logic out of the component (for cleaner code).
  
---

## 8. What is the useLayoutEffect hook and how is it different from useEffect?
The useLayoutEffect hook is similar to useEffect, but it fires synchronously after all DOM mutations, before the browser paints the screen.

This means:
- useLayoutEffect runs after React updates the DOM, but before the user sees it.
- useEffect runs after the paint.

So, use useLayoutEffect when you need to:
- Read layout or DOM measurements (getBoundingClientRect, etc.)
- Make DOM changes that must happen before the screen updates (e.g., animations, positioning)

**Difference between useEffect and useLayoutEffect:**

| useEffect     |        	   useLayoutEffect |
|----------------|-------------------------------|
| Runs after paint	     |    Runs before paint |
| Async (non-blocking UI)	|   Sync (can block paint) |

Used in most cases	Used when precise layout tweaks are needed

---

## 9. What is the useImperativeHandle hook and when is it used?
- useImperativeHandle is a React hook that allows a child component to expose specific methods or properties to its parent via ref.
- It’s used with forwardRef to give controlled access — for example, exposing a focusInput function to the parent without revealing the whole child component’s internals.

Normally, refs expose the DOM node. But with useImperativeHandle, you can control what gets exposed — for example, a custom function like focus().

Syntax:
```
import { useImperativeHandle, forwardRef, useRef } from 'react';

const MyInput = forwardRef((props, ref) => {
  const inputRef = useRef();

  useImperativeHandle(ref, () => ({
    focusInput: () => {
      inputRef.current.focus();
    },
  }));

  return <input ref={inputRef} />;
});
```
Then in the parent:
```
const ref = useRef();
<MyInput ref={ref} />
ref.current.focusInput(); // Custom exposed method
```
Use case:
When the parent needs to call imperative methods (e.g., .focus(), .scrollTo(), .reset()), but the child is a custom component, not a regular DOM node.

### What is forwardRef?
- Normally, ref only works with DOM elements (like <input /> or <div />), not with custom components.
- forwardRef allows a parent component to pass a ref into a child component, so that the parent can directly interact with a DOM element inside the child.

---

## 10. What is the useId hook and what problem does it solve?
The useId hook in React is used to generate a unique ID that is consistent across the server and client, especially useful for accessibility attributes like id, aria-labelledby, htmlFor, etc.

It was introduced in React 18 to help with hydration mismatches during server-side rendering (SSR).
```
const id = useId();
<input id={id} />
<label htmlFor={id}>Name</label>
```
Even if the component renders multiple times or in different environments (client/server), the ID will remain stable and unique.

---
## 11. What is the useTransition hook in React?
The useTransition hook is used to mark a state update as non-urgent (or "low priority"), allowing React to keep the UI responsive during heavy or slow updates.
- useTransition is a React hook that lets you mark state updates as non-urgent.
It allows React to prioritize more important updates first (like user input) and delay slower ones (like rendering large components), improving responsiveness.

It helps in improving performance and user experience when rendering large lists, filtering data, or doing anything that might cause a delay.
```
const [isPending, startTransition] = useTransition();

startTransition(() => {
  setSomeSlowState(value);
});
```
**startTransition:** Wrap your non-urgent update inside this.

isPending: A boolean that tells you if the transition is still ongoing (can be used to show a loader/spinner).

✅ Use Case Example:
If you’re filtering a huge list of items:
```
const handleChange = (e) => {
  const input = e.target.value;
  startTransition(() => {
    setFilteredList(filterList(input));
  });
};
```
This keeps the typing smooth and responsive even if filtering is slow.
---
## 12. What does the useDeferredValue hook do, and when might you use it?
The useDeferredValue hook is used to defer updating a value until the browser has time to handle it, keeping the UI fast and responsive — especially when dealing with expensive rendering tasks.
- useDeferredValue is a React hook that delays updating a value until the browser is less busy.
It helps improve performance by deferring non-urgent updates, like filtering large lists, while keeping urgent updates like typing fast and responsive.

It's useful when you have a value (like input text) that updates quickly, but the UI based on it (like a large filtered list) is slow to render.

Syntax:
```
const deferredValue = useDeferredValue(value);
```
You can use deferredValue instead of value in the slow-rendering part of your UI.

Example Use Case:
```
const [input, setInput] = useState('');
const deferredInput = useDeferredValue(input);

const filteredList = useMemo(() => {
  return bigList.filter(item => item.includes(deferredInput));
}, [deferredInput]);
```
This way, the input updates instantly, and the filtering is deferred — preventing lag.

- Use these hooks when you need to set priority
- If you have control over the state update — useTransition.
- For third party update where you have no control over state — useDeferredValue.
  
---
## 13. What is the useSyncExternalStore hook and when would you use it?
The useSyncExternalStore hook is used to subscribe to an external store and ensure consistent state between server and client — especially in concurrent rendering.

It was introduced in React 18 to replace legacy subscription patterns and make external data sources more compatible with React’s rendering model.
```
const state = useSyncExternalStore(
  subscribe,         // how to subscribe to the store
  getSnapshot,       // how to get the current value (for client)
  getServerSnapshot  // (optional) for SSR
);
```
Use Case:
You’d use this hook when:
- You're integrating Redux or Zustand manually (without their hooks).
- You're building a custom global store.
- You want a React-compatible way to listen to non-React state (like browser storage, WebSocket, etc.).
---
## 14. What does the useInsertionEffect hook do, and when would you use it?
useInsertionEffect is a React hook used to inject styles or modify the DOM before layout effects (useLayoutEffect) and before the browser paints the screen.

It’s primarily intended for CSS-in-JS libraries to insert styles synchronously — avoiding flickering or visual glitches.
```
useInsertionEffect(() => {
  // Insert styles or mutate DOM before layout phase
}, []);
```
Use Case:
- Libraries like styled-components, emotion, or tailwind-in-js may use it internally.
- If you're building a UI library and need to inject styles in the correct order and timing.

React itself recommends avoiding this hook unless you're writing a low-level library that modifies DOM styles.



