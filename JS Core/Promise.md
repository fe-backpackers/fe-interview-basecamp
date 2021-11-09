# 프로미스란?

## 결론

- 자바스크립트 비동기 처리에 사용되는 객체입니다.

## 설명

- 비동기 처리 시 서버에 요청한 데이터가 오기도 전에 렌더링하면 오류가 발생합니다. 콜백함수로 이런 비동기 처리 문제점을 처리합니다.
- 서버에 요청하는 횟수가 많아지면서 콜백지옥에 빠지게 됩니다. 프로미스는 이런 콜백지옥을 해결해줍니다.
- pending 상태에서 요청이 성공하면 resolve에 담아 반환하고 실패하면 reject에 담아 반환합니다. then으로 resolve 값을 사용하고, catch로 reject 값을 사용합니다.

## 요약

- then과 catch로 프로미스 객체를 연결해서 비동기 처리를 컨트롤합니다.

## 레퍼런스

- https://joshua1988.github.io/web-development/javascript/promise-for-beginners/
