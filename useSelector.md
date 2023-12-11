Redux - отдельная библиотека для работы с централизованным состоянием приложения.
Паттерн программирования Flux
Позволяет перенести бизнес логику отдельно от React

![image](https://github.com/lmambl/Hooks/assets/127667945/b89b56ac-caa1-4daa-a053-0577baecdd33)

Store - общее хранилище, может быть только 1. Имеет функцию для создания стора, контейнера состояний.
Папка redux - там хранится наше состояние.
(createStore)

Как и в случае с connect(), вам следует обернуть все ваше приложение в компонент <Provider>, чтобы сделать хранилище доступным во всём дереве компонентов:
combine
```js
const store = createStore(rootReducer)

// Начиная с React 18
const root = ReactDOM.createRoot(document.getElementById('root'))
root.render(
  <Provider store={store}>
    <App />
  </Provider>
)
```

```js
const rootReducer = combineReducers({
key:value
}
```

useStore принимает ()=> у него store, который нужно типизировать :RootState

const something= useSelector((store:RootState)=>store.somethingRerducerKey.somethingValue)

![image](https://github.com/lmambl/Hooks/assets/127667945/75a46f47-85cb-4f24-8cc6-8468b40e5782)

const dispathc = useDispatch() - идет от store , типизируем dispatch в store


