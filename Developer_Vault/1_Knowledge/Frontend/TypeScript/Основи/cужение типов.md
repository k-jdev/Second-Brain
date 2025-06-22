Предположим, что у нас имеется функция под названием `padLeft`:

``` ts
function padLeft(padding: number | string, input: string): string {
  throw new Error('Еще не реализовано!')
}
```

Если `padding` - это `number`, значит, мы хотим добавить указанное количество пробелов перед `input`. Если `padding` - это `string`, значит, мы просто хотим добавить `padding` перед `input`. Попробуем реализовать логику, когда `padLeft` принимает `number` для `padding`:

```ts
function padLeft(padding: number | string, input: string): string {
  return new Array(padding + 1).join(' ') + input
  // Operator '+' cannot be applied to types 'string | number' and 'number'.
  // Оператор '+' не может быть применен к типам 'string | number'
}
```

Мы получаем ошибку. `TS` предупреждает нас о том, что добавление `number` к `number | string` может привести к неожиданному результату, и он прав. Другими словами, мы должны проверить тип `padding` перед выполнением каких-либо операций с ним:

```ts
function padLeft(padding: number | string, input: string): string {
  if (typeof padding === 'number') {
    return new Array(padding + 1).join(' ') + input
  }
  return padding + input
}
```



Теги:: #programming