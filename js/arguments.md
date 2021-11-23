# arguments 객체란?

## 결론

- arguments 객체란 함수 호출시에 암시적으로 전달되는 매개변수로서, 함수의 모든 매개변수들에 대한 참조값을 가진 유사배열객체입니다.

## 설명

- JS에서는 함수 호출시 전달하는 매개변수의 갯수가 함수 선언시의 매개변수의 갯수와 일치하지 않아도 됩니다.

- 따라서 함수 선언시의 매개변수의 갯수보다 더 많은 수의 매개변수를 함수 호출시 전달한 경우에 arguments 객체를 이용하여 참조할 수 있습니다.

- arguments 객체는 유사배열객체이기 때문에 `Array.prototype`의 메서드를 사용할 수 없습니다.

- 화살표 함수는 자체적인 arguments 객체를 가지고 있지 않기 때문에, 화살표 함수에서 arguments 객체에는 화살표 함수를 둘러싼 최근접 일반 함수의 arguments 객체의 참조값이 할당됩니다.

## 요약

- arguments 객체란 함수 호출시에 암시적으로 전달되는 매개변수로서, 함수에 전달된 모든 매개변수들에 대한 참조값을 가진 유사배열객체입니다.

## Further Step

- arguments vs rest parameter: strict mode에서는 arguments 객체의 값을 변경하더라도 반영되지 않고, 최초 호출 상태를 반영합니다.

## Reference

- <https://velog.io/@bigsaigon333/%EB%AA%A8%EB%8D%98-%EC%9E%90%EB%B0%94%EC%8A%A4%ED%81%AC%EB%A6%BD%ED%8A%B8-%ED%95%A8%EC%88%98>
