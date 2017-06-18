# Operacje na kolekcjach - `find()`, `every()`, `some()`

nowe metody `Array.prototype` z ES6

Wraz z `ECMAScript 6` obiekt `Array` zyskał nowe metody:

* `Array.find()` - pozwala wyszukać pojedynczy element tablicy,

* `Array.every()` - sprawdza czy każdy element tablicy spełnia zadany warunek,

* `Array.some()` - sprawdza czy conajmniej jeden element tablicy spełnia zadany warunek.


## `find()`

##### [Przykład 2.4.1](https://codepen.io/mmotel/pen/BZpJXW)
```js
const id = 3;
const foundStudent = 
    students.filter(student => student.id === id)[0];

foundStudent.log(); 
// -> (3) Marisol Sargent
```

##### [Przykład 2.4.2](https://codepen.io/mmotel/pen/mwRXdP)
```js
const id = 3;
const foundStudent = students.find(student => student.id === id);

foundStudent.log(); 
// -> (3) Marisol Sargent
```

## `every()`

##### [Przykład 2.4.3](https://codepen.io/mmotel/pen/JJEpoQ)
```js
let areAllStudentsActive = 
    students.reduce((acc, student) => acc && student.isActive, true);

console.log(areAllStudentsActive); // -> false
```

##### [Przykład 2.4.4](https://codepen.io/mmotel/pen/KqaQpo)
```js
let areAllStudentsActive = 
    students.every(student => student.isActive);

console.log(areAllStudentsActive); // -> false
```

## `some()`

##### [Przykład 2.4.5](https://codepen.io/mmotel/pen/awpqmg)
```js
let isAnyoneWithBlueEyes = students
    .filter(student => student.eyeColor === 'blue')
    .length > 0;

console.log(isAnyoneWithBlueEyes); // -> false
```

##### [Przykład 2.4.6](https://codepen.io/mmotel/pen/mwRXRO)
```js
let isAnyoneWithBlueEyes = 
    students.some(student => student.eyeColor === 'blue');

console.log(isAnyoneWithBlueEyes); // -> false
```

---

###### Źródła

* https://developer.mozilla.org/pl/docs/Web/JavaScript/Referencje/Obiekty/Array/Find
* https://developer.mozilla.org/pl/docs/Web/JavaScript/Referencje/Obiekty/Array/Every
* https://developer.mozilla.org/pl/docs/Web/JavaScript/Referencje/Obiekty/Array/Some