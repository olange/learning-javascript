# Learning Javascript

Learning more about Javascript – articles, useful resources, personal notes.

## Quick reference

* **[`function*`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/function*) declaration** defines a generator function, which returns a [`Generator`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Generator) object. The returned `Generator` object conforms to both the [iterable protocol](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Iteration_protocols#The_iterable_protocol) and the [iterator protocol](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Iteration_protocols#The_iterator_protocol) (ES2015).
* **[`yield`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/yield) keyword** is used to pause and resume a [generator function](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/function*) (`function*`). `[rv] = yield [expression];` _expression_ defines the value to return from the generator function via the iterator protocol; _rv_ returns the optional value passed to the generator's `next()` method to resume its execution. (ES2015)
* **[`yield*`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/yield*) expression** is used to delegate to another [generator function](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/function*) or [iterable object](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Iteration_protocols#The_iterable_protocol). `yield* [[expression]];` _expression_ is the expression that returns an iterable object. (ES2015)
