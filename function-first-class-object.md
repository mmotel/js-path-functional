# Funkcja - obiekt pierwszej klasy

JavaScript jest językiem obiektowo-funkcyjnym. Jego twórca, Brendan Eich, miał za zadanie stworzyć język, który będzie `Scheme` w przedlądarce oraz będzie wyglądał jak `Java`. 

![](/assets/brendan-eich.jpg)

W JavaScript wszystko jest obiektem, również funkcja. A dokładniej funkcje są obiektami pierwszej klasy. Oznacza to, że możemy z nimi zrobić dokładnie to samo co z innymi obiektami. Ważną cechą funkcji jest to, że mogą zostać wywołane przy użyciu `()`.

Możemy przypisać funkcję do zmiennej.

##### [Przykład 1.1](https://codepen.io/mmotel/pen/awpxYj)
```js
let greet = function (name) {
    return `Hello, my name is ${name}.`;
}
```

Możemy przekazać funkcję jako parametr do innej funkcji.

##### [Przykład 1.2](https://codepen.io/mmotel/pen/XgpQqq)
```js
const name = 'John Doe';

function greeter (greet) {
    console.log(greet(name));
}
```

Możemy również zwrócić funkcję jako wynik innej funkcji.

##### [Przykład 1.3](https://codepen.io/mmotel/pen/WORWyR)
```js
function createGreeter () {
    return function (name) {
        return `Hello, my name is ${name}.`;
    }
}
```

Własność `length` obiektu funkcji pozwala sprawdzić ilość jej formalnych argumentów.

##### [Przykład 1.4](https://codepen.io/mmotel/pen/XgRMGV)
```js
function greet (name, age, city) {
  return `My name is ${name}, I am ${age} years old and from ${city}.`;
}

console.log( greet.length ); // -> 3
```

#### Funkcje wyższego poziomu

Funkcje wyższego pozioku (z ang. _high order functions_) są funkcjami, które przyjmują inne funkcje jako argumenty.

##### [Przykład 1.5](https://codepen.io/mmotel/pen/JJrZjN)
```js
function applyAction (numbers, action) {
  for (let number of numbers) {
    action(number);
  }
}

applyAction([1, 2, 3, 4], console.log);
```

Dzięki wykorzystaniu podejścia funkcyjnego możemy sprawić, że nasz kod stanie się bardziej czytelny, łatwiejszy w utrzymaniu i ponownym wykorzystaniu.

Załóżmy, że mamy tablicę liczb od 1 do 10. Chcemy wypisać liczby parzyste. Zacznijmy od wersji imperatywnej.

###### [Przykład 1.6](https://codepen.io/mmotel/pen/awYaQQ)
```js
const numbers = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10];

for (let num of numbers) {
  if (num % 2 === 0) {
    console.log(num);
  }
}
// -> 2
// -> 4
// -> 6
// -> 8
// -> 10
```

Zobaczmy jak wygląda wersja funkcyjna tego kodu.

##### [Przykład 1.7](https://codepen.io/mmotel/pen/xrWaMM)
```js
const numbers = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10];

function printNumbers (numbers, printer, condition) {
  numbers.forEach(num => {
    if (condition(num)) {
      printer(num);
    }
  });
}

const isEven = num => num % 2 === 0;

printNumbers(numbers, console.log, isEven);
```

Ta wersja zapewnia nam dużą elastyczność. Możemy dowolnie sterować  działaniem funkcji `printNumbers()` podczas jej wywoływania. Dodatkowo wersja funkcyjna spełnia zasadę _RSP_ - (ang. _single responsibility principle_). Funkcja _isEven()_ ma jedno i tylko jedno zadanie - sprawdzić czy liczba jest parzysta. Podobnie funckja _printNumbers()_ zajmuje się wypisaniem liczb. Nie skupia się nad tym w jaki sposób je wypisać ani na tym, które z nich. 

## Czego brakuje w JavaScript?

Jednak JavaScript nie jest w pełni językiem funkcyjnym. Brakuje mu kliku ważnych elementów.

* czystych funkcji - _pure functions_ - czyli funkcji bez efektów ubocznych, np. `console.log()`,

* niezmiennego stanu - możemy wykorzystać  `const` czy też `Object.freez()` ,

* _tail call optimization_ - JavaScript wspiera rekursję ale nie obsługuje poprawnie optymalizacji rekursji.

## O czym będziemy mówić

Będziemy mówili o tym jak wykorzystać elementy programowania funkcyjnego aby nasz kod w JavaScript stał się bardziej czytelny oraz reużywalny.

Przyjrzymy się:

* przetwarzaniu potokowym na przykładzie kolekcji,
* programowaniu reaktywnym na przykładzie `RxJS` i `Observables`.
