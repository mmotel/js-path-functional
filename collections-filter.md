# Operacje na kolekcjach - `filter()`

imperative

##### [Przykład 2.2.1](https://codepen.io/mmotel/pen/NgbNpL)
```js
let activeStudents = [];

for (let student of students) {
  if (student.isActive) {
    activeStudents.push(student);
  }
}

console.log(activeStudents);
// -> (0) Christina Richmond
// -> (2) Viola Shelton
```

.forEach() version

##### [Przykład 2.2.2](https://codepen.io/mmotel/pen/MobyQN)
```js
let activeStudents = [];

students.forEach(student => {
  if (student.isActive) {
    activeStudents.push(student);
  }
});

log(activeStudents);
// -> (0) Christina Richmond
// -> (2) Viola Shelton
```

2-3 examples

##### [Przykład 2.2.3](https://codepen.io/mmotel/pen/YQpqLr)
```js
let activeStudents = students.filter(student => student.isActive);

log(activeStudents);
// -> (0) Christina Richmond
// -> (2) Viola Shelton
```

##### [Przykład 2.2.4](https://codepen.io/mmotel/pen/qjqZKR)
```js
let studentsFrom1B = students
  .filter(student => student.classes.filter(c => c === '1B').length > 0);

log(studentsFrom1B);
// -> (1) Austin Wooten
// -> (3) Marisol Sargent
// -> (4) Hawkins Everett
```

task

## combine .map() and .filter()

.forEach() version

##### [Przykład 2.2.5](https://codepen.io/mmotel/pen/XgNKpM)
```js
let namesWithN = [];
    
students.forEach(student => {
  let name = student.firstName;
  if (name.toLowerCase().indexOf('n') > 0) {
    namesWithN.push(name);
  }
});

console.log(namesWithN);
// -> ["Christina", "Austin", "Hawkins"]
```


##### [Przykład 2.2.6](https://codepen.io/mmotel/pen/GENqqw)
```js
let namesWithN = students
  .map(student => student.firstName)
  .filter(name => name.toLowerCase().indexOf('n') > 0);

console.log(namesWithN);
// -> ["Christina", "Austin", "Hawkins"]
```

task 