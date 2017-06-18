# Funkcja - _obywatel_ pierwszej klasy

JavaScript jest językiem obiektowo-funkcyjnym. Jego twórca, Brendan Eich, miał za zadanie stworzyć język, w którym będą `Scheme` w przedlądarce oraz będzie wyglądał jak `Java`. 

W JavaScript wszystko jest obiektem, również funkcja. A dokładniej funkcje w JavaScript są "obywatelami" pierwszej klasy. Oznacza to, że możemy z nimi zrobić dokładnie to samo co z innymi obketami.

Możemy przypisać funkcję do zmiennej.

```js
var greet = function (name) {
    return `Hello, my name is ${name}.`;
}
```

Możemy przekazać funkcję jako parametr do innej funkcji.

```js
const name = 'John Doe';

function greeter (greet) {
    console.log(greet(name));
}
```

Możemy również zwrócić funkcję jako wynik innej funkcji.

```js
function createGreeter () {
    return function (name) {
        return `Hello, my name is ${name}.`;
    }
}
```


