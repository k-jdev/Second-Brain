Что если мы хотим использовать один и тот же тип в нескольких местах? Для этого используются синонимы типов:

```ts
type Point = {
  x: number
  y: number
}

// В точности то же самое, что в приведенном выше примере
function printCoords(pt: Point) {
  console.log(`Значение координаты 'x': ${pt.x}`)
  console.log(`Значение координаты 'y': ${pt.y}`)
}

printCoords({ x: 3, y: 7 })
```

Синонимы можно использовать не только для объектных типов, но и для любых других типов, например, для объединений:

``` ts
type ID = number | string
```

<span style="background:#ff4d4f">> Обратите внимание!</span>
> Синонимы - это всего лишь синонимы, мы не можем создавать на их основе другие "версии" типов. Например, такой код может выглядеть неправильным, но `TS` не видит в нем проблем, поскольку оба типа являются синонимами одного и того же типа:


```ts
type UserInputSanitizedString = string

function sanitizeInput(str: string): UserInputSanitizedString {
  return sanitize(str)
}

// Создаем "обезвреженный" инпут
let userInput = sanitizeInput(getInput())

// По-прежнему имеем возможность изменять значение переменной
userInput = 'new input'
```




Теги:: #programming