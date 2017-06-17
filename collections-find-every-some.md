# Operacje na kolekcjach - `find()`, `every()`, `some()`

nowe metody `Array.prototype` z ES6

## `find()`

##### [Przykład 2.4.1](https://codepen.io/mmotel/pen/BZpJXW)
```js
const id = 3;
const foundStudent = 
    students.filter(student => student.id === id)[0];

console.log(foundStudent);
```

##### [Przykład 2.4.2](https://codepen.io/mmotel/pen/mwRXdP)
```js
const id = 3;
const foundStudent = students.find(student => student.id === id);

console.log(foundStudent);
```

## `every()`

##### [Przykład 2.4.3](https://codepen.io/mmotel/pen/JJEpoQ)
```js
let areAllStudentsActive = 
    students.reduce((acc, student) => acc && student.isActive, true);

console.log(areAllStudentsActive);
```

##### [Przykład 2.4.4](https://codepen.io/mmotel/pen/KqaQpo)
```js
let areAllStudentsActive = 
    students.every(student => student.isActive);

console.log(areAllStudentsActive);
```

## `some()`

---

###### Źródła

* https://developer.mozilla.org/pl/docs/Web/JavaScript/Referencje/Obiekty/Array/Find
* https://developer.mozilla.org/pl/docs/Web/JavaScript/Referencje/Obiekty/Array/Every
* https://developer.mozilla.org/pl/docs/Web/JavaScript/Referencje/Obiekty/Array/Some