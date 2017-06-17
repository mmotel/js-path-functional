# Operacje na kolekcjach - `reduce()`

.forEach\(\) version

##### [Przykład 2.3.1](https://codepen.io/mmotel/pen/YQppNZ)

```js
let sumOfAges = 0;

students.forEach(student => {
  sumOfAges += student.age;
});

console.log(sumOfAges); // -> 110
```

##### [Przykład 2.3.2](https://codepen.io/mmotel/pen/KqNNmJ)

```js
let sumOfAges = students
  .reduce((acc, student) => acc += student.age, 0);

console.log(sumOfAges);
```

2-3 examples  
finding max/min value

##### [Przykład 2.3.3](https://codepen.io/mmotel/pen/YQppEQ)

```js
let maxAge = students
  .reduce(
    (acc, student) => acc && acc >= student.age ? acc : student.age,
    null
  );

console.log(maxAge); // -> 26
```

converting array to object

##### [Przykład 2.3.4](https://codepen.io/mmotel/pen/OgbbvE)

```js
let studentsDict = students
  .reduce(
    (acc, student) => { 
      acc[student.id] = student; 
      return acc; 
    }, 
    {}
  );

console.log(studentsDict);
// {
//    0: Student {id: 0, firstName: "Christina", lastName: "Richmond", …},
//    1: Student {id: 1, firstName: "Austin", lastName: "Wooten", …},
//    2: Student {id: 2, firstName: "Viola", lastName: "Shelton", …},
//    3: Student {id: 3, firstName: "Marisol", lastName: "Sargent", …},
//    4: Student {id: 4, firstName: "Hawkins", lastName: "Everett", …}
// }
```

task

## combine .map\(\) and .reduce\(\)

.forEach\(\) version

##### [Przykład 2.3.5](https://codepen.io/mmotel/pen/OgbWze)

```js
let allClasses = [];

students.forEach(student => {
  student.classes.forEach(c => {
    allClasses.push(c);
  });
});

console.log(allClasses);
// -> ["1A", "Art", "1B", "Science", "1A", "Science", 
//     "1B", "Music", "1B", "Art", "Music"]

let uniqueClasses = new Set(allClasses);

console.log(uniqueClasses);
// -> Set {"1A", "Art", "1B", "Science", "Music"}
```

##### [Przykład 2.3.6](https://codepen.io/mmotel/pen/MobJXp)

```js
let allClasses = students
  .map(student => student.classes)
  .reduce((acc, classes) => acc.concat(classes), []);

console.log(allClasses);
// -> ["1A", "Art", "1B", "Science", "1A", "Science", 
//     "1B", "Music", "1B", "Art", "Music"] 

let uniqueClasses = new Set(allClasses);

console.log(uniqueClasses);
// -> Set {"1A", "Art", "1B", "Science", "Music"}
```

task

## combine .map\(\) .reduce\(\) and .filter\(\)

.forEach\(\) version

##### [Przykład 2.3.7](https://codepen.io/mmotel/pen/KqNaEa)

```js
let adultsNames = '';

students.forEach(student => {
  if (student.age >= 21) {
    adultsNames += `${student.firstName} ${student.lastName}, `;
  }
});

console.log(adultsNames);
// -> 'Austin Wooten, Marisol Sargent, Hawkins Everett, '
```

##### [Przykład 2.3.8](https://codepen.io/mmotel/pen/owYBRJ)

```js
let adultsNames = students
  .filter(student => student.age >= 21)
  .map(student => `${student.firstName} ${student.lastName}`)
  .reduce((acc, name) => acc ? `${acc}, ${name}` : name, '');

console.log(adultsNames);
// -> 'Austin Wooten, Marisol Sargent, Hawkins Everett'
```

task

## .reduce\(\) tricks

.map\(\) implementation

##### [Przykład 2.3.9](https://codepen.io/mmotel/pen/OgbpmX)

```js
function map (array, mapper) {
  return array
    .reduce((acc, item) => acc.concat([mapper(item)]), []);
}

let studentAges = map(students, student => student.age);

console.log(studentAges);
// -> [19, 21, 20, 26, 24]
```

.filter\(\) implementation

##### [Przykład 2.3.10](https://codepen.io/mmotel/pen/vZyxeE)

```js
function filter (array, condition) {
  return array.reduce(
    (acc, item) => condition(item) ? acc.concat([item]) : acc, 
    []
  );
}

let adultStudents = filter(students, student => student.age >= 21);

log(adultStudents);
// -> (1) Austin Wooten
// -> (3) Marisol Sargent
// -> (4) Hawkins Everett
```

---

##### Źródła

* [https://developer.mozilla.org/pl/docs/Web/JavaScript/Referencje/Obiekty/Array/Reduce](https://developer.mozilla.org/pl/docs/Web/JavaScript/Referencje/Obiekty/Array/Reduce)



