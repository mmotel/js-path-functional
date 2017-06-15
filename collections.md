# Operacje na kolekcjach

W ES5 mamy jeden typ reprezentujący kolekcje - `Array`. Razem z ES6 zyskaliśmy dwa kolejne `Set`oraz`Map`. Programowanie funkcyjne znacznie ułatwia operowanie na nich.

W przykładach będziemy korzystali z tablicy `students`, przechowującej instanceje klasy `Student`.

```js
class Student {
  constructor ({id, firstName, lastName, age, eyeColor,
                isActive, classes}) {
    this.id = id,
    this.firstName = firstName,
    this.lastName= lastName,
    this.age = age,
    this.eyeColor = eyeColor,
    this.isActive = isActive,
    this.classes = classes
  }
  
  toString () {
    return `(${this.id}) ${this.firstName} ${this.lastName}`;
  }
  
  log (...fields) {
    console.log(`${this}${this.logFields(fields)}`);
  }
  
  logFields (fields) {} // -> field=value...
}
```

Tak wyglądają dane naszych studentów.

```js
const students = [
  new Student({
    "id": 0,
    "firstName": "Christina",
    "lastName": "Richmond",
    "age": 19,
    "eyeColor": "green",
    "isActive": true,
    "classes": ["1A", "Art"]
  }),
  new Student({
    "id": 1,
    "firstName": "Austin",
    "lastName": "Wooten",
    "age": 21,
    "eyeColor": "blue",
    "isActive": false,
    "classes": ["1B", "Science"]
  }),
  new Student({
    "id": 2,
    "firstName": "Viola",
    "lastName": "Shelton",
    "age": 20,
    "eyeColor": "blue",
    "isActive": true,
    "classes": ["1A", "Science"]
  }),
  new Student({
    "id": 3,
    "firstName": "Marisol",
    "lastName": "Sargent",
    "age": 26,
    "eyeColor": "brown",
    "isActive": false,
    "classes": ["1B", "Music"]
  }),
  new Student({
    "id": 4,
    "firstName": "Hawkins",
    "lastName": "Everett",
    "age": 24,
    "eyeColor": "blue",
    "isActive": false,
    "classes": ["1B", "Art", "Music"]
  })
];
```

## Iteracja

Podstawową operacją na kolekcji jest wykonanie na niej iteracji.

```js
for(let i = 0; i < students.length; i += 1) {
  console.log(students[i]);
}
```

Można nieco usprawnić ciało pętli tworząc zmienną `student`, która przechowuje element tablicy, który nas aktualnie interesuje.

```js
for(let i = 0; i < students.length; i += 1) {
  let student = students[i];
  console.log(student);
}
```

Korzystając z metody `Array.forEach()` możemy skupić się na tym co chcemy zrobić z elementami tablicy, a nie na tym jak po niej iterować.

```js
students.forEach(student => {
  console.log(student);
});
```

Metoda `Array.forEach()` przekazuje do funkcji obsługującej trzy parametry: element tablicy, jego indeks oraz całą tablicę.

```js
students.forEach( (student, index, students) => {
  console.log(student, index, students);
});
```

---

###### Źródła

* https://developer.mozilla.org/pl/docs/Web/JavaScript/Referencje/Obiekty/Array/forEach