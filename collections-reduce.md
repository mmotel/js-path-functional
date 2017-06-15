# Operacje na kolekcjach - `reduce()`

.forEach() version

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

## combine .map() and .reduce()

.forEach() version

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

## combine .map() .reduce() and .filter()

.forEach() version

2 -3 examples

task

## .reduce() tricks

.map() implementation

.filter() implementation


