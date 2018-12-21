# Learning Javascript

Learning more about Javascript – articles, useful resources, personal notes.

## Quick reference

### Promises

* [MDN › Javascript Guides › Using Promises](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Using_promises) All about their guarantees, chaining them, error propagation, composition, timing (passed-in functions are put on microtask queue, they never run immediately), nesting and common mistakes
* Remember: `then()` expects a *function* (or two); that returns either a `Promise`; a scalar; or throws ([We have a problem with promises — Common mistakes with promises](https://t.co/rZyuKREaUW), Nolan Lawson, 18.05.2015)

### Iteration protocols

* [Iterable protocol](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Iteration_protocols#The_iterable_protocol) To be iterable, an object must implement the `@@iterator` method — meaning that the object (or one of the objects up its [prototype chain](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Inheritance_and_the_prototype_chain)) must have a property with a `@@iterator` key, which is available via constant [`Symbol.iterator`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Symbol/iterator). The method `@@iterator` is a zero arguments function, that returns an object, conforming to the [iterator protocol](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Iteration_protocols#The_iterator_protocol). (ES2015)
* [Iterator protocol](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Iteration_protocols#The_iterator_protocol) An object is an iterator, when it implements a `next()` method with the following semantics: a zero arguments function, that returns an object with at least the following two properties:
  * `done` – a boolean with either the value _true_, if the iterator is past the end of the iterated sequence — in this case `value` optionally specifies the return value of the iterator; or the value _false_, if the iterator was able to produce the next value in the sequence; this is equivalent of not specifying the done property altogether.
  * `value` – any JavaScript value returned by the iterator. Can be omitted when done is true. (ES2015)

### Generators

* **[`function*`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/function*) declaration** defines a generator function, which returns a [`Generator`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Generator) object. The returned `Generator` object conforms to both the [iterable protocol](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Iteration_protocols#The_iterable_protocol) and the [iterator protocol](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Iteration_protocols#The_iterator_protocol) (ES2015).
* **[`yield`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/yield) keyword** is used to pause and resume a [generator function](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/function*) (`function*`). `[rv] = yield [expression];` _expression_ defines the value to return from the generator function via the iterator protocol; _rv_ returns the optional value passed to the generator's `next()` method to resume its execution. (ES2015)
* **[`yield*`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/yield*) expression** is used to delegate to another [generator function](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/function*) or [iterable object](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Iteration_protocols#The_iterable_protocol). `yield* [[expression]];` _expression_ is the expression that returns an iterable object. (ES2015)

### Web- and Service Workers

* [Learning Service Workers](https://olange.github.io/learning-service-workers/) experiments, articles, reading notes
* [Learning Service Workers › Reading notes › The Basics of Web Workers ](https://github.com/olange/learning-service-workers/issues/2)
