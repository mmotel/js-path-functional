# Programowanie reaktywne

interactive vs reactive programming

![](/assets/interactive_vs_reactive.png)

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
    
Observable.from()
    
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
    
 map
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

filter
##### [Przykład 3.4](https://codepen.io/mmotel/pen/YQQorW)
```js
Rx.Observable.from([1, 2, 3, 4])
   .filter(item => item % 2 === 0)
   .subscribe(observer);
// -> 'next: 2'
// -> 'next: 4'
// -> 'complete'

```
    
do
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

merge
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

take
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
fromEvent
##### [Przykład 2.8](https://codepen.io/mmotel/pen/RggzzZ)
```js
Rx.Observable.fromEvent(window, 'mousemove')
   .subscribe(observer);
```

##### [Przykład 2.9](https://codepen.io/mmotel/pen/gRRNVo)
```js
Rx.Observable.fromEvent(window, 'mousemove')
   .map(event => ({x: event.clientX, y: event.clientY}))
   .filter(position => position.x < 200 && position.y < 200)
   .subscribe(observer);
```

event handling
catch
##### [Przykład 2.10](https://codepen.io/mmotel/pen/mwMWqL)
```js
Rx.Observable.fromEvent(window, 'mousemove')
   .map(event => ({
      x: event.clientX, 
      y: event.clientY, 
      z: event.client.zIndex
   }))
   .catch(error => { 
      console.log(`catched error: ${error.message}`); 
      return Rx.Observable.of({x: 0, y:0, z: 0}); 
   })
   .subscribe(observer);
```

creating your own observables
Observable.of()

##### [Przykład 3.11](https://codepen.io/mmotel/pen/RgZVGv)
```js
Rx.Observable.create(observer => {
   observer.next(1);
   observer.next(2);
   observer.next(3);
   observer.next(4);
   observer.complete();
})
.subscribe(observer);
```

forkJoin
##### [Przykład 3.12](https://codepen.io/mmotel/pen/YQxVYg)
```js
let stream1$ = Rx.Observable.create(observer => {
   observer.next(1);
   observer.complete();
});

let stream2$ = Rx.Observable.create(observer => {
   setTimeout(() => {
      observer.next(2);
      observer.complete();
   }, 1000);
});

Rx.Observable
   .forkJoin(stream1$, stream2$)
   .subscribe(observer);
```

flatMap
##### [Przykład 3.13](https://codepen.io/mmotel/pen/zzdwRR)
```js
let stream1$ = Rx.Observable.of(3);

let stream2$ = (count) => Rx.Observable.create(observer => {
   for(let i = 0; i < count; i += 1) {
      observer.next(i);
   }
   observer.complete();
});

stream1$
   .flatMap(count => stream2$(count))
   .subscribe(observer);
```

---

###### Źródła

* http://reactivex.io/learnrx/
* https://xgrommx.github.io/rx-book/why_rx.html
* http://reactivex.io/documentation/observable.html
* [https://medium.com/@benlesh/learning-observable-by-building-observable](https://medium.com/@benlesh/learning-observable-by-building-observable-d5da57405d87)