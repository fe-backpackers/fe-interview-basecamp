# 커링이란?

## 결론

- 커링이란 여러 개의 인자를 받는 함수가 있을 때, 각각의 인자를 함수 호출의 형태로 받아두었다가 인자가 원하는 개수가 되었을 때 받아두었던 함수를 평가시키는 함수로 변환시키는 기법입니다.

```js
// 얕은 커리
const curry =
  (f) =>
  (a, ...as) =>
    as.length > 0 ? f(a, ...as) : (...bs) => f(a, ...bs);

// 깊은 커리
const curry2 = (f) =>
  function curried(...as) {
    return as.length >= f.length ? f(...as) : (...bs) => curried(...as, ...bs);
  };

const mult = curry((a, b) => a * b);

console.log(mult(1, 3));
console.log(mult(1)(3));

const mult2 = curry2((a, b, c, d) => a * b * c * d);

console.log(mult2(1)(2)(3, 4));
console.log(mult2(1, 2)(3, 4));
```

## 설명

- JS에서는 함수가 일급객체여서 값으로 다룰 수 있기 때문에 커링이 가능합니다.

- 클로저로 인해 내부 함수가 외부 함수의 변수를 외부 함수 호출이 완료된 이후에도 참조 가능합니다.

## 요약

- 커링이란 함수를 값으로 다루면서 인자로 받은 함수를 원하는 시점에 평가시키는 함수입니다.
