# Events & EventEmitter in Node.js

Node.js is **event-driven**, meaning much of its core functionality relies on **emitting and listening for events**. This is made possible through the built-in `events` module and its `EventEmitter` class.

---

## Importing EventEmitter

```js
const EventEmitter = require('events');
const emitter = new EventEmitter();
```
Emitting Events
```
emitter.emit('greet');
```
This triggers any listener attached to the 'greet' event.

### Listening to Events
```
emitter.on('greet', () => {
  console.log('Hello there!');
});
```
Now when emitter.emit('greet') is called, the above function runs.

### Passing Arguments
```
emitter.on('userLoggedIn', (username) => {
  console.log(`${username} has logged in.`);
});

emitter.emit('userLoggedIn', 'Divyanshi');
```
### Listening Once
```
emitter.once('onceEvent', () => {
  console.log('This will only run once!');
});

emitter.emit('onceEvent'); // Runs
emitter.emit('onceEvent'); // Ignored
```
### Removing Listeners
```
const greetUser = () => console.log('Hello again!');
emitter.on('greet', greetUser);

// Remove it
emitter.removeListener('greet', greetUser);
```
Or use:
```
emitter.off('greet', greetUser);
```
### Checking Listeners
```
console.log(emitter.listenerCount('greet')); // Number of listeners
```
## Real-World Use Cases

- Server listening to requests
- File upload progress tracking
- Chat applications
- Notifications

### Example
```
const EventEmitter = require('events');
const myEmitter = new EventEmitter();

myEmitter.on('dataReceived', (data) => {
  console.log(`Received: ${data}`);
});

myEmitter.emit('dataReceived', 'Hello from Node!');
```
