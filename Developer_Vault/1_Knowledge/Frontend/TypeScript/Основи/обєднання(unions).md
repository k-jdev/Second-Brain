Це тип, який створений з 2 або більше типів, який присвоює один з цих типів значенню
```ts
function printId(id: number | string) {
  console.log(`Ваш ID: ${id}`)
}

// OK
printId(101)
// OK
printId('202')
// Ошибка
printId({ myID: 22342 })
// Argument of type '{ myID: number }' is not assignable to parameter of type 'string | number'. Type '{ myID: number }' is not assignable to type 'number'. Аргумент типа '{ myID: number }' не может быть присвоен параметру типа 'string | number'. Тип '{ myID: number }' не может быть присвоен типу 'number'
```




Теги:: #programming