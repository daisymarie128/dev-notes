## Concurrency, and the Event Loop
In Javascript concurrency is achieved through something called the ***event loop***. A JavaScript application can handle concurrent operations on a single thread, by putting events in things like queues and tasks etc.


#### Definitions:
- **Concurrency:** the execution of several instruction sequences at the same time.


### Tasks, Mircrotasks, Scheduals, Queues.

```js
const makePromise = new Promise((resolve, reject) => {
  console.log('make promise');

  setTimeout(function() {
    console.log('setTimeout');
    Promise.resolve();
  }, 0);
})

makePromise(1).then(function() {
  console.log('promise 1');
})

makePromise(2).then(function() {
  console.log('promise 2');
})
```

***In what order should the logs appear?***<br>
make Promise<br>
make promise<br>
setTimeout<br>
promise 1<br>
setTimeout<br>
promise 2

### Node
Node doesn’t have a microtask queue, unlike most browsers.