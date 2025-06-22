Например, когда мы используем `document.getElementById`, `TS` знает лишь то, что данный метод возвращает какой-то `HTMLElement`, но мы знаем, например, что будет возвращен `HTMLCanvasElement`. В этой ситуации мы можем использовать утверждение типа для определения более конкретного типа:

```ts
const myCanvas = document.getElementById('main_canvas') as HTMLCanvasElement
```




Теги:: #programming