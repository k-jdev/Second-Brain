Функция `createReducer()` похожа на функцию создания поисковой таблицы из документации по `Redux`. В ней используется библиотека `immer`, что позволяет писать "мутирующий" код, обновляющий состояние иммутабельно. Это защищает от непреднамеренного мутирования состояния в редукторе.

Ниже приводится пример использования `createReducer()`. Начнем с типичного редуктора для списка задач, в котором используется инструкция `switch` и иммутабельные обновления:
```js
function todosReducer(state = [], action) {
  switch (action.type) {
    case 'ADD_TODO': {
      return state.concat(action.payload)
    }
    case 'TOGGLE_TODO': {
      const { index } = action.payload
      return state.map((todo, i) => {
        if (i !== index) return todo

        return {
          ...todo,
          completed: !todo.completed
        }
      })
    }
    case 'REMOVE_TODO': {
      return state.filter((todo, i) => i !== action.payload.index)
    }
    default:
      return state
  }
}
```
