# Node.js Architecture

Understanding how Node.js works under the hood is key to writing efficient and scalable applications. Node.js uses a non-blocking, event-driven architecture built on the **Chrome V8 JavaScript engine**.

---

## 🧠 How Node.js Works

When a client makes a request to the Node.js server:

1. The request is received by the **Event Loop**.
2. If the request is simple (e.g., a calculation), it's handled directly.
3. If it involves I/O (file system, DB, etc.), it's sent to the **Worker Pool**.
4. Once the result is ready, a **callback** is triggered and added to the **Callback Queue**.
5. The **Event Loop** then picks up the callback and sends the response to the client.

---

## 🧩 Key Components

| Component | Description |
|----------|-------------|
| **V8 Engine** | Converts JavaScript code to machine code. |
| **Event Loop** | Handles all asynchronous operations in a single-threaded way. |
| **Event Queue** | Holds the incoming requests to be processed. |
| **Worker Pool (libuv)** | Manages threads for expensive I/O tasks. |
| **libuv** | A C++ library that handles the event loop, I/O, and thread pool. |
| **Callback Queue** | Stores callbacks waiting to be executed after async tasks finish. |

---

## 🔁 Event Loop Phases

Node.js executes tasks in a specific sequence using phases:

1. **Timers** – Executes `setTimeout()` and `setInterval()`.
2. **Pending Callbacks** – Executes I/O callbacks deferred to the next loop.
3. **Idle, Prepare** – Internal use.
4. **Poll** – Retrieves new I/O events, executes I/O-related callbacks.
5. **Check** – Executes `setImmediate()` callbacks.
6. **Close Callbacks** – Executes close events like `socket.on('close', ...)`.

---

## 📊 Visual Representation
       ┌────────────────────────┐
       │    Incoming Request    │
       └────────────┬───────────┘
                    ▼
           ┌──────────────┐
           │  Event Loop  │
           └──────┬───────┘
                  ▼
     ┌────────────────────────────┐
     │       Is it blocking?      │
     └───────┬─────────────┬──────┘
             ▼             ▼
    ┌─────────────┐   ┌───────────────┐
    │ Process Now │   │ Send to Thread│
    │  (Main Loop)│   │   Pool (libuv)│
    └─────────────┘   └───────────────┘


---

## 🎯 Why It's Powerful

- Handles **thousands of requests** with a single thread.
- Ideal for I/O-heavy operations.
- Doesn’t wait for one task to finish before moving to the next.

---

## 🚫 Not Ideal For

- CPU-intensive tasks like large computations.
  (Use worker threads or offload to another service.)

---

## 🧪 Try It Yourself

```js
console.log("Start");

setTimeout(() => {
  console.log("Inside setTimeout");
}, 0);

console.log("End");

// Output:
// Start
// End
// Inside setTimeout


