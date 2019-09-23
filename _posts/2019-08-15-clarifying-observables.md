---
layout: post
title: Clarifying RxJS Observables under 5 minutes
published: true
date: 2019-08-15 15:09:00
description: Clarifying RxJS Observables under 5 minutes
tags: javascript, angular, beginners, webdev
cover_image: https://thepracticaldev.s3.amazonaws.com/i/clyed2rfu51t23bd6mrm.png
canonical_url: https://blog.craftlab.hu/clarifying-observables-b7b3ed7e0a5f
---

Most people, including myself, meet [RxJS] observables for the first time when starting to develop [Angular] applications. [Observables] are the essential elements of the framework; you can’t do too many things without using them. For example, [HTTP requests][Angular Http] return their results as an Observable. This way, you can think that it is just another fancy variation for [Promises] and don’t use them for anything else. If you do this, sometimes weird things will happen: HTTP requests are running multiple times or never when they should be, or things happen in random order. In this tutorial, I’ll show you how I managed to understand how Observables work and make development with Angular more productive and relaxing.

### Promises

Starting to look at HTTP requests in Angular as an alternative Promise implementation can be a good starting point and a misleading one as well. Their API is somewhat similar, as both provide success and failure callbacks for listening to results and errors.

```javascript
const observable = api.callWithObservable();
const promise = api.callWithPromise();

observable.subscribe(
  result => { /* on success */ },
  error => { /* on error */ }
);

promise.then(
  result => { /* on success */ },
  error => { /* on error */ }
);
```

We start the operation with a function call, and the returned Observable/Promise emits the result/error later in time. The similarities begin and end here. Everything else - execution, number of results, and behavior - differs.

### Multiple results

While a Promise only emits the result once, Observables can emit multiple values over time.

```javascript
const observable = Rx.Observable.interval(1000).take(5);

observable.subscribe(
  result => console.log(result),
  error => { /* on error */ },
  () => { /* on complete */ }
);
```

In the above example, the Observable emits the values 0,1,2,3,4 delayed by one second and then completes. The subscribe method is called five times, and besides its values, we can also detect the end of the stream. On completion, the third callback gets called inside the subscribe function. After that, the Observable won't emit values.

Emitting values over time makes Observables very similar to streams (for example in Node.js). You might have found out that they also have similar methods like merging two separate streams or buffering (merge, buffer).

### Synchronous execution

When a promise is resolved, the then callback is called asynchronously. Inside the Javascript event loop, the then callbacks will be executed in the next cycle. In contrary, the subscriptions of an Observable will be executed synchronously after a value is passed in.

```javascript
let promiseResult;
Promise.resolve(15).then(val => { 
  promiseResult = val;
  console.log('resolved promise', val);
});
console.log('result promise', promiseResult); // result promise undefined

let observableResult;
Rx.Observable.of(15).subscribe(val => {
  observableResult = val;
  console.log('resolved observable', val);
});
console.log('result observable', observableResult); // result observable 15
```

If you run this example, you will see that the value assigned inside the then callback is still undefined when we print it with console.log. On the other hand, the value inside the subscribe callback won't be undefined, and it will be printed out by console.log.

This synchronous execution also goes for Subjects when calling the next method.

```javascript
const subject = new Rx.Subject();

let observableResult;
subject.subscribe(val => {
  observableResult = val;
  console.log('resolved observable', val);
});

subject.next(15);
console.log('result observable', observableResult); // result observable 15
```

The resolved log will appear before the result in the console because it iterates through all the subscriptions synchronously.

### Multiple executions

Have you experienced that things get weird when subscribing to an Observable multiple times? Like being executed multiple times, for example with an HTTP request?

It is because, when the subscribe method is called, a separate execution is created for the observable. And if that execution consists of an HTTP request, the endpoint will be called again.

```javascript
const observable = Rx.Observable.interval(1000).take(5);

observable
  .subscribe(x => console.log('A next ' + x)); // create an execution

setTimeout(() => {
  observable
    .subscribe(x => console.log('B next ' + x)); // create an execution
}, 2000);

// A next 0
// A next 1
// B next 0
// A next 2
// B next 1
// A next 3
```

We would expect that the second subscription (B), which arrives after 2 seconds, receives the same values as the first subscription. But in reality, B gets the values from the start, just delayed with 2 seconds. The reason behind this is that every subscribe method creates a new execution, restarting the observable separately from the previous one.

Promises won't restart when you write multiple then methods to the same promise; they execute asynchronously and get the same value. To create the same behavior with Observables we have to apply the share operator, which gives the same execution for every subscription. In the background, the operator creates a Subject and pass the values onto that.

### Array methods

While Promises has only the then method to mutate the returned value, Observables have multiple methods for it. These methods are named very similar to array methods.

```javascript
promise
  .then(value => value + 5)
  .then(value => Promise.resolve(9));

observable.pipe(
  map(value => value + 5),
  flatMap(value => Rx.Observable.of(9)),
  filter(value => value > 5)
);
```

Inside the then method, you can either return a new value or a new promise. It acts the same; the next then method gets the value returned previously. With Observables, we have to separate synchronous (map) and asynchronous (flatMap) transformation. Observables also have many array methods (filter, reduce, join, includes, etc.) and array methods from utility libraries (Lodash: pluck, groupBy, etc.)

### Still not clear?

WWhen I was learning Observables, [the RxMarbles site][RxMarbles] was the one that made them crystal clear. RxMarbles are graphical representations on a timeline describing the behavior of an Observable composition. Different colors mean different events coming from sources and how they behave, for example, when we merge them.

![RxMarbles](https://thepracticaldev.s3.amazonaws.com/i/clyed2rfu51t23bd6mrm.png)

### Summary

Through Promises it is possible to understand Observables, but you have to know the differences:

- Multiple values over time
- Synchronous callbacks
- Multiple executions
- Array-like methods

Hopefully, the above comparisons have clarified the misunderstandings and obscure parts of Observables. For further learning, I would recommend reading the [blog of André Staltz][Andre Staltz] (core contributor of RxJS) and listening to his [tutorials on Egghead][Egghead tutorials].

[RxJS]: https://rxjs-dev.firebaseapp.com
[Observables]: https://rxjs-dev.firebaseapp.com/guide/observable
[Angular]: https://angular.io/
[Promises]: https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Promise
[Angular Http]: https://angular.io/guide/http
[Andre Staltz]: https://staltz.com/blog.html
[Egghead tutorials]: https://egghead.io/instructors/andre-staltz
[RxMarbles]: https://rxmarbles.com/
