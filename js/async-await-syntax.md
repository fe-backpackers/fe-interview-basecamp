# async-await 란?

## 결론

- `async-await`는 Promise 기반의 비동기 함수를 읽고 쓰기 편하게 만들어주는 syntatic sugar입니다.

## 설명

- ES8에 도입된 문법으로서, `async-await`를 사용하면 비동기 함수를 마치 동기 함수인 것처럼 작성할 수 있습니다.

- 비동기 함수를 호출하는 외부 함수의 선언시 `async` 키워드를 붙이며, 비동기 함수 호출시 `await` 키워드를 붙여서 작성합니다.

- `await` 키워드를 붙인 비동기 함수 호출의 경우, 비동기 연산이 성공한 경우에는 `fulfilled` 프로미스의 값을 반환하며, 비동기 연산이 실패한 경우에는 `rejected` 프로미스의 값을 `throw`합니다. 따라서 예외처리 시에 동기함수와 동일하게 try - catch 문을 사용할 수 있습니다.

- `async` 함수는 항상 `Promise`를 반환합니다. `async` 함수 내의 return 값은 `Promise`로 감싸져서 반환됩니다.

- 만약 `async` 함수 내에서 예외가 발생하였고 이를 try - catch 문으로 핸들링하지 않았다면, throw 된 예외를 값으로 가지는 `rejected` 프로미스가 반환됩니다.

## 요약

- `async-await`는 `Promise`기반의 비동기 함수를 마치 동기함수와 같은 흐름으로 읽고 쓰게 해주는 문법입니다.

## Further Step

- top-level await

## Reference

- https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/async_function

- https://developer.mozilla.org/en-US/docs/Learn/JavaScript/Asynchronous/Async_await
