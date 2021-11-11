# Arguments 객체란?

## 결론

- 함수에 전달된 인수를 값으로 가지는 배열 형태의 객체입니다.

## 설명

- 함수에 전달된 모든 인수는 arguments라는 이름을 가진 객체에 저장됩니다. arguments 객체는 배열과 같은 인덱스를 가집니다.
- 배열 형태의 객체로 배열과 같은 방법으로 접근하여 사용할 수 있고 length 메소드를 사용할 수 있습니다. 배열이 아니기 때문에 배열 메소드는 사용할 수 없습니다.
- 함수에 선언된 파라미터 개수보다 더 많은 인수로 함수를 호출하는 경우 arguments 객체를 사용하여 나머지 인수에 접근할 수 있습니다.

## 요약

- ES6 명세의 나머지 매개변수와 같은 목적으로 ESNext 전에 나머지 인수를 사용하는 객체입니다.

## 레퍼런스

- https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Functions/arguments
- http://taewan.kim/tip/argument_parameter/
- https://velog.io/@lilyoh/js-argument-%EA%B0%9D%EC%B2%B4
