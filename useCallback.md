useCallback - это хук React, который позволяет кэшировать определение функции между повторными рендерингами.
по совей сути синтаксическая обертка useMemo для для кэширования колбэк-функции.

```js
const cachedFn = useCallback(fn, dependencies);
```
```js
import { useCallback } from 'react';

export default function ProductPage({
    productId,
    referrer,
    theme,
}) {
    const handleSubmit = useCallback(
        (orderDetails) => {
            post('/product/' + productId + '/buy', {
                referrer,
                orderDetails,
            });
        },
        [productId, referrer]
    );
    // ...
}
```
Принимает:
```js
/*Значение функции, которое вы хотите кэшировать. Она может принимать любые аргументы и возвращать любые значения.
React вернет (не вызовет!) вашу функцию обратно во время первоначального рендера. При последующих рендерах React вернет вам ту же функцию,
если зависимости не изменились с момента последнего рендера. В противном случае, он отдаст вам функцию, которую вы передали во время
текущего рендеринга, и сохранит ее на случай, если она может быть использована позже. React не будет вызывать вашу функцию.
Функция возвращается вам, чтобы вы могли решить, когда и стоит ли ее вызывать.
dep*/
```
Возвращает: 
```js
При первоначальном рендере useCallback возвращает переданную вами функцию fn.
При последующих рендерах она либо вернет уже сохраненную функцию fn из последнего рендера
(если зависимости не изменились), либо вернет функцию fn, которую вы передали во время этого рендера.
```
