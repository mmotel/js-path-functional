# Operacje na kolekcjach - `map()`

imperative

##### [Przykład 2.1.1](https://codepen.io/mmotel/pen/mwOeoN)
```js
let names = [];

for (let student of students) {
  names.push(`${student.firstName} ${student.lastName}`);
}

console.log(names);
// -> ["Christina Richmond", "Austin Wooten", 
//     "Viola Shelton", "Marisol Sargent", "Hawkins Everett"]
```

.forEach() version

##### [Przykład 2.1.2](https://codepen.io/mmotel/pen/VWmeEv)
```js
let names = [];

students.forEach(student => {
  names.push(`${student.firstName} ${student.lastName}`);
});

console.log(names);
// -> ["Christina Richmond", "Austin Wooten", 
//     "Viola Shelton", "Marisol Sargent", "Hawkins Everett"]
```

2 examples

##### [Przykład 2.1.3](https://codepen.io/mmotel/pen/rwWxQP)
```js
let names = students
  .map(student => `${student.firstName} ${student.lastName}`);

console.log(names);
// -> ["Christina Richmond", "Austin Wooten", 
//     "Viola Shelton", "Marisol Sargent", "Hawkins Everett"]
```

##### [Przykład 2.1.4](https://codepen.io/mmotel/pen/pwNgBO)
```js
let eyeColors = students.map(student => student.eyeColor);

console.log(eyeColors);
// -> ["green", "blue", "blue", "brown", "blue"]

let uniqueEyeColors = new Set(eyeColors);

console.log(uniqueEyeColors);
// -> Set {"green", "blue", "brown"}
```

task 

---

###### Źródła

* https://developer.mozilla.org/pl/docs/Web/JavaScript/Referencje/Obiekty/Array/map
