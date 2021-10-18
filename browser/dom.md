## 결론

html을 파싱하여 브라우저가 이해할 수 있는 구조로 구성하여 메모리에 적재하는 것을 DOM이라고 합니다

## 설명

- DOM은 모델의 객체에 접근하고 변경할 수 있는 DOM API를 제공합니다. 이 DOM API는 프로퍼티와 메서드를 가지고 있습니다
- Dom tree는 브라우저가 HTML을 받아서 파싱하여 생성하는 모델을 의미합니다. 객체의 트리로 구조화되어 있기 때문에 DOM tree라고 부릅니다
- HTML 요소가 중첩되면서 부자관계가 형성되는데 이런한 HTML 요소 간의 부자 관계를 반영하여 노드 객체들로 트리 자료 구조를 구성합니다

## 요약

html을 모든 요소, 요소의 어트리뷰트, 텍스트를 각각의 객체로 만들고 이 객체들의 부자 관계를 트리 구조로 구성한 것이 DOM입니다. DOM은 자바스크립트를 통해 동적으로 변경할 수 있고 변경된 DOM은 렌더링에 반영됩니다

## 참고글

[DOM 소개](https://developer.mozilla.org/ko/docs/Web/API/Document_Object_Model/Introduction)

[poiemaweb - DOM](https://poiemaweb.com/js-dom)
