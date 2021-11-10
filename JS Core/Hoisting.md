# 호이스팅이란?

## 결론

- 코드가 실행되기 전 실행 컨텍스트를 형상화하는 과정에서 모든 선언을 메모리에 저장하는 것입니다.

## 설명

- var 키워드로 선언한 변수는 선언과 동시에 undefined로 초기화되고, let 키워드와 const 키워드로 선언한 변수는 초기화되지 않고 선언만 됩니다.
- 함수 선언은 선언 자체가 함수 생성을 의미하기 때문에 그대로 저장됩니다.
- 실행 컨텍스트가 구조와 되고 나면 초기화된 변수와 함수 선언은 스코프 내 어디에서도 참조할 수 있습니다. 다른 선언들은 선언만 된 상태이기 때문에 참조에러(ReferenceError)가 발생합니다.

## 요약

- var 키워드로 선언한 변수와 함수 선언문으로 생성한 함수는 스코프 내 어디에서도 참조할 수 있습니다.

## 레퍼런스

- https://developer.mozilla.org/ko/docs/Glossary/Hoisting
- https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Statements/function
- https://hanamon.kr/javascript-%ED%98%B8%EC%9D%B4%EC%8A%A4%ED%8C%85%EC%9D%B4%EB%9E%80-hoisting/
