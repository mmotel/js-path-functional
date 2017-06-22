# Programowanie reaktywne

interactive vs reactive programming

everything is a stream


## RxJS

MSFT libarary 
reactive extensions

> Think of RxJS as Lodash for events.

## observer - subscriber pattern

## Observable

Observable
    
##### [Przykład 3.1](https://codepen.io/mmotel/pen/gRRNbM)
```js
Rx.Observable.from([1, 2, 3, 4])
   .subscribe(item => { 
      console.log(`item: ${item}`); 
   });
// -> 'item: 1'
// -> 'item: 2'
// -> 'item: 3'
// -> 'item: 4'
```
    
    
Observer
    next error complete
    
##### [Przykład 3.2](https://codepen.io/mmotel/pen/weeLJq)
```js
let observer = {
   next: item => { console.log(`next: ${item}`); },
   error: err => { console.log(`error: ${err}`); },
   complete: () => { console.log(`complete`) }
};

Rx.Observable.from([1, 2, 3, 4])
   .subscribe(observer);
// -> 'next: 1'
// -> 'next: 2'
// -> 'next: 3'
// -> 'next: 4'
// -> 'complete'
```

Operators
    map filter do merge retry
    
##### [Przykład 3.3](https://codepen.io/mmotel/pen/jwwjwx)
```js
Rx.Observable.from([1, 2, 3, 4])
   .map(item => item * item)
   .subscribe(observer);
// -> 'next: 1'
// -> 'next: 4'
// -> 'next: 9'
// -> 'next: 16'
// -> 'complete'
```

##### [Przykład 3.4](https://codepen.io/mmotel/pen/YQQorW)
```js
Rx.Observable.from([1, 2, 3, 4])
   .filter(item => item % 2 === 0)
   .subscribe(observer);
// -> 'next: 2'
// -> 'next: 4'
// -> 'complete'

```
    
##### [Przykład 3.5](https://codepen.io/mmotel/pen/KqqjyB)
```js
Rx.Observable.from([1, 2, 3, 4])
   .do(item => { console.log(`do: ${item}`); })
   .subscribe(observer);
// -> 'do: 1'
// -> 'next: 1'
// -> 'do: 2'
// -> 'next: 2'
// -> 'do: 3'
// -> 'next: 3'
// -> 'do: 4'
// -> 'next: 4'
// -> 'complete'
```

##### [Przykład 3.6](https://codepen.io/mmotel/pen/KqqjyB)
```js
let stream1$ = Rx.Observable.from([1, 2, 3, 4]);
let stream2$ = Rx.Observable.from(['a', 'b', 'c']);

stream1$
   .merge(stream2$)
   .subscribe(observer);
// -> 'next: 1'
// -> 'next: 2'
// -> 'next: 3'
// -> 'next: 4'
// -> 'next: a'
// -> 'next: b'
// -> 'next: c'
// -> 'complete'
```

##### [Przykład 3.7](https://codepen.io/mmotel/pen/dRRBwp)
```js
Rx.Observable.from([1, 2, 3, 4])
   .take(2)
   .subscribe(observer);
// -> 'next: 1'
// -> 'next: 2'
// -> 'complete'
```

examples for asynchronous actions

event handling

handling http requests

```js
.catch()
```

```js
.forkJoin()
```

```js
.flatMap()
```
creating your own observables

```js
Observable.of()
```

```js
Observable.create()
```

---

###### Źródła

* http://reactivex.io/learnrx/
* https://xgrommx.github.io/rx-book/why_rx.html
* http://reactivex.io/documentation/observable.html
* [https://medium.com/@benlesh/learning-observable-by-building-observable](https://medium.com/@benlesh/learning-observable-by-building-observable-d5da57405d87)