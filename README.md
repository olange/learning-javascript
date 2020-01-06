# Learning Javascript

Learning more about Javascript – articles, useful resources, personal notes.

## Quick reference

### Fundamentals

* [Tips for common idioms](TIPS.md) _accessing property values while protecting from inexistent properties, and suggestions for other day-to-day idioms_
* [2ality › Global scope](https://2ality.com/2019/07/global-scope.html) _How do JavaScript’s global variables really work? All about_ scopes, lexical environments, global object, global environment, module environments
* [Mathias Bynens › Notes on `globalthis`](https://mathiasbynens.be/notes/globalthis)
* [Lydia Hallie › JavaScript Visualized: Prototypal Inheritance](https://dev.to/lydiahallie/javascript-visualized-prototypal-inheritance-47co)

### Pull vs Push

Pull and Push are two different protocols that describe how a data _Producer_ can communicate with a data _Consumer_.

| System |	Single value	| Multiple values | Description |
|---|---|---|---|
| [Pull](https://rxjs-dev.firebaseapp.com/guide/observable#pull-versus-push) |	**[Function](https://developer.mozilla.org/en-US/docs/Glossary/Function)** |	**[Iterator](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Iteration_protocols#The_iterator_protocol)** | The _Consumer_ determines when it receives data from the data _Producer_. The _Producer_ itself is unaware of when the data will be delivered to the _Consumer_. |
| [Push](https://rxjs-dev.firebaseapp.com/guide/observable#pull-versus-push) |	**[Promise](https://developer.mozilla.org/en-US/docs/Mozilla/JavaScript_code_modules/Promise.jsm/Promise)** | **[Observable](https://rxjs-dev.firebaseapp.com/guide/observable)** | The _Producer_ determines when to send data to the _Consumer_. The _Consumer_ is unaware of when it will receive that data. |

### Promises

* [MDN › Javascript Guides › Using Promises](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Using_promises) All about their guarantees, chaining them, error propagation, composition, timing (passed-in functions are put on microtask queue, they never run immediately), nesting and common mistakes
* Remember: `then()` expects a *function* (or two); that returns either a `Promise`; a scalar; or throws ([We have a problem with promises — Common mistakes with promises](https://t.co/rZyuKREaUW), Nolan Lawson, 18.05.2015)

### Observables / RxJS

* [`Observable`](https://rxjs-dev.firebaseapp.com/guide/observable) Observables are lazy push collections of multiple values. Represent the idea of an invokable collection of future values or events. `const observable = Observable.create( function (observer) { … })` The code of the ellipsis represents an _Observable execution_, a lazy computation that only happens for each `Observer` that subscribes. The execution produces multiple values over time, either synchronously or asynchronously.
* `Observers` – a collection of callbacks, that knows how to listen to values delivered by the Observable. An `Observer` is an object with methods `next( value)`, `error( err)`, `complete()`. `observable.subscribe( observer)` is the way to start an _Observable execution_ and deliver values or events to the Observer of that execution. In an _Observable Execution_, zero to infinite Next notifications may be delivered; if either an Error or Complete notification is delivered, then nothing else can be delivered afterwards.
* [`Subscription`](https://rxjs-dev.firebaseapp.com/guide/subscription) – an object that represents a disposable resource, usually the execution of an `Observable`; is primarily useful for cancelling the execution. Has one important method, `unsubscribe()`, that takes no argument and just disposes the resource held by the subscription.
* [`Subject`](https://rxjs-dev.firebaseapp.com/guide/subject) – a special type of Observable, that allows values to be _multicasted_ to many Observers. While plain Observables are _unicast_ — each subscribed `Observer` owns an _independent execution_ of the `Observable` —, Subjects are _multicast_. The equivalent to an `EventEmitter`.
* Operator – pure function that enables a functional programming style of dealing with collections, with operations like `map`, `filter`, `concat`, `reduce`, …
* `Scheduler` – centralized dispatchers to control concurrency, allowing to coordinate when computation happens, on e.g. `setTimeout` or `requestAnimationFrame` or others.

### Iteration protocols

* [Iterable protocol](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Iteration_protocols#The_iterable_protocol) To be iterable, an object must implement the `@@iterator` method — meaning that the object (or one of the objects up its [prototype chain](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Inheritance_and_the_prototype_chain)) must have a property with a `@@iterator` key, which is available via constant [`Symbol.iterator`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Symbol/iterator). The method `@@iterator` is a zero arguments function, that returns an object, conforming to the [iterator protocol](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Iteration_protocols#The_iterator_protocol). (ES2015)
* [Iterator protocol](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Iteration_protocols#The_iterator_protocol) An object is an iterator, when it implements a `next()` method with the following semantics: a zero arguments function, that returns an object with at least the following two properties:
  * `done` – a boolean with either the value _true_, if the iterator is past the end of the iterated sequence — in this case `value` optionally specifies the return value of the iterator; or the value _false_, if the iterator was able to produce the next value in the sequence; this is equivalent of not specifying the done property altogether.
  * `value` – any JavaScript value returned by the iterator. Can be omitted when done is true. (ES2015)

### Generators

* **[`function*`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/function*) declaration** defines a generator function, which returns a [`Generator`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Generator) object. The returned `Generator` object conforms to both the [iterable protocol](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Iteration_protocols#The_iterable_protocol) and the [iterator protocol](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Iteration_protocols#The_iterator_protocol) (ES2015).
* **[`yield`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/yield) keyword** is used to pause and resume a [generator function](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/function*) (`function*`). `[rv] = yield [expression];` _expression_ defines the value to return from the generator function via the iterator protocol; _rv_ returns the optional value passed to the generator's `next()` method to resume its execution. (ES2015)
* **[`yield*`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/yield*) expression** is used to delegate to another [generator function](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/function*) or [iterable object](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Iteration_protocols#The_iterable_protocol). `yield* [[expression]];` _expression_ is the expression that returns an iterable object. (ES2015)

### Streams

* [Learning using Streams, Observables and Transforms](https://github.com/olange/learning-streams/) articles, useful resources, personal notes

### Web- and Service Workers

* [Learning Service Workers](https://olange.github.io/learning-service-workers/) experiments, articles, reading notes
* [Learning Service Workers › Reading notes › The Basics of Web Workers ](https://github.com/olange/learning-service-workers/issues/2)
* **[`Transferable`]() interface** represents an object that can be transfered between different execution contexts, like the main thread and Web workers. The [`ArrayBuffer`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/ArrayBuffer), [`MessagePort`](https://developer.mozilla.org/en-US/docs/Web/API/MessagePort) and [`ImageBitmap`](https://developer.mozilla.org/en-US/docs/Web/API/ImageBitmap) types implement this interface.
* **[`ArrayBuffer`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/ArrayBuffer) object** is used to represent a generic, fixed-length _raw binary_ data buffer. You cannot directly manipulate its contents; instead, you create one of the [typed array objects](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/TypedArray) or a [`DataView`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/DataView) object which represents the buffer in a specific format, and use that to read and write the contents of the buffer.
* **[`ImageBitmap`](https://developer.mozilla.org/en-US/docs/Web/API/ImageBitmap) interface** represents a bitmap image which can be drawn to a `<canvas>` without undue latency; it can be created from a variety of source objects, using the [`createImageBitmap()`](https://developer.mozilla.org/en-US/docs/Web/API/ImageBitmapFactories/createImageBitmap) factory method. `ImageBitmap` provides an asynchronous and resource efficient pathway to prepare textures for rendering in WebGL.
