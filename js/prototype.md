# 프로토타입이란?

## 결론

- 프로토타입 객체란 메서드와 프로퍼티를 상속하는 객체를 의미합니다.

## 설명

- 모든 객체는 프로토타입 객체를 가지지만, null일 수도 있습니다.
- 생성자의 인스턴스는 생성자의 `prototype` 프로퍼티를 프로토타입 객체로 가집니다.


## 요약

- 프로토타입 객체란 **메서드와 속성을 상속하는 객체**로서, 모든 객체는 자신의 프로토타입 객체를 참조하는 내부 프로퍼티를 가지고 있습니다.

## Further Step

- 프로토타입 체인

---

# 프로토타입 체인이란?

## 결론

- 프로토타입 체인은 객체와 객체의 프로토타입을 묶는 체인으로서, 프로토타입 체인에 의해서 객체는 프로토타입 체인 내에 존재하는 프로퍼티에 접근 가능합니다.

## 설명

- 객체의 프로퍼티에 접근할 때 JS는 그 객체에서 프로퍼티 검색을 시작해서, 프로퍼티가 존재하지 않으면 프로토타입 객체로, 프로토타입 객체에도 프로퍼티가 존재하지 않으면 프로토타입 객체의 프로토타입 객체로 검색을 확장합니다. 즉, 프로토타입 체인을 거슬러서 검색합니다. 프로토타입 체인을 이용해서 마치 단일 객체인 것처럼 행동합니다.
- 객체에 직접 정의된 프로퍼티는 고유 프로퍼티(`own property`)이며, 프로토타입 체인을 통해 접근가능한 프로퍼티는 상속한 프로퍼티(`inherited property`)라고 부릅니다.
- 프로토타입 체인 내 정의된 메서드를 호출시, 메서드 내 `this`는 메서드를 소유한 객체(홈 객체)가 아니라 실제 메서드를 호출한 객체입니다.
- 프로토타입 체인 전체를 검색하는 건 프로퍼티를 읽을 때 뿐입니다. 프로퍼티를 설정하거나 삭제할 때는 상속을 무시하고, 고유 프로퍼티에만 영향을 미칩니다. 즉, 프로토타입 체인 내의 프로퍼티와 동명의 프로퍼티를 설정하면 프로토타입 체인 내의 프로퍼티는 변경시키지 않고, 고유 프로퍼티를 추가합니다. 또한 프로퍼티를 삭제할 때(`delete` 연산자 사용), `delete` 연산자는 `true`를 반환하지만 상속한 프로퍼티는 삭제되지 않습니다.

## 요약

- 프로토타입 체인은 객체와 객체의 프로토타입을 묶는 체인으로서, 객체는 프로토타입 체인에 의해 프로토타입 체인 내에 존재하는 메서드와 프로토타입에 모두 접근 가능합니다.

## Reference

- [https://ko.javascript.info/prototype-inheritance](https://ko.javascript.info/prototype-inheritance)
- [https://developer.mozilla.org/en-US/docs/Learn/JavaScript/Objects/Object_prototypes](https://developer.mozilla.org/en-US/docs/Learn/JavaScript/Objects/Object_prototypes)
- [https://developer.mozilla.org/en-US/docs/Web/JavaScript/Inheritance_and_the_prototype_chain](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Inheritance_and_the_prototype_chain)
- [https://velog.io/@bigsaigon333/object-prototype-in-js](https://velog.io/@bigsaigon333/object-prototype-in-js)
- [Prototype, 그리고 Class](https://tecoble.techcourse.co.kr/post/2021-06-14-prototype/)
