# Operacje na kolekcjach

W ES5 mamy jeden typ reprezentujący kolekcje - `Array`. Razem z ES6 zyskaliśmy dwa kolejne `Set`oraz`Map`. Programowanie funkcyjne znacznie ułatwia operowanie na nich.

W przykładach będziemy korzystali z tablicy `students`.

```js
const students = [
  {
    "id": 0,
    "firstName": "Christina",
    "lastname": "Richmond",
    "age": 19,
    "eyeColor": "green",
    "isActive": true,
    "classes": ["1A", "Art"]
  },
  {
    "id": 1,
    "firstName": "Austin",
    "lastName": "Wooten",
    "age": 21,
    "eyeColor": "blue",
    "isActive": false,
    "classes": ["1B", "Science"]
  },
  {
    "id": 2,
    "firstName": "Viola",
    "lastName": "Shelton",
    "age": 20,
    "eyeColor": "blue",
    "isActive": true,
    "classes": ["1A", "Science"]
  },
  {
    "id": 3,
    "firstName": "Marisol",
    "lastName": "Sargent",
    "age": 26,
    "eyeColor": "brown",
    "isActive": false,
    "classes": ["1B", "Music"]
  },
  {
    "id": 4,
    "firstName": "Hawkins",
    "lastName": "Everett",
    "age": 24,
    "eyeColor": "blue",
    "isActive": false,
    "classes": ["1B", "Art", "Music"]
  }
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