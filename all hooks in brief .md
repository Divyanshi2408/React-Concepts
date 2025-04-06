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



