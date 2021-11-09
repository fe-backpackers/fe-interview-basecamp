# 프로토타입이란?

## 결론

- 객체 안에서 다른 객체를 상속하는 방법입니다.

## 설명

- 자바스크립트는 함수를 사용하여 상속을 구현합니다. 자바스크립트의 함수는 객체입니다.
- 함수로 객체를 정의할 때 다른 객체에서 참조할 수 있는 로직을 생성하여 prototype에 저장할 수 있습니다. 상속받는 객체는 상속하는 객체의 prototype에 접근하여 사용합니다.
- 다른 객체를 상속받아 생성된 객체에서는 \_\_proto\_\_ 파라미터를 이용하여 상위 객체의 prototype에 연결됩니다.

## 요약

- prototype에 상속할 로직을 정의하고 \_\_proto\_\_ 파라미터로 연결하여 사용하는 자바스크립트 상속 방법입니다.

## 레퍼런스

- https://www.youtube.com/watch?v=RYxgNZW3wl0
- https://opentutorials.org/module/532/6573
- https://www.youtube.com/watch?v=wT1Bl5uV27Y
