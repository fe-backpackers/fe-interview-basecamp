# JSX란?

## 결론

- 함수 호출로 컴파일되는 XML과 유사한 표현식으로, React에서 UI가 어떻게 생겼는지를 나타내기 위해 사용되는 문법입니다.

## 설명

- JSX는 JavaScript Syntax Extension 의 줄임말입니다.

- React에서는 각 VDOM요소(UI의 각 요소)를 React Element라고 하며, JSX는 React Element를 생성합니다.

- JSX는 markup language 처럼 생겼지만 JS이기 때문에 JS의 모든 기능을 사용할 수 있습니다.
    - 예시: attribute의 값으로 JS 원시 타입을 할당하거나, 이벤트 핸들러로 JS 함수를 등록하는 것이 가능합니다.
    - 다만, JSX 안에서 표현식을 사용하기 위해서는 중괄호로 표현식을 감싸야 합니다.

- JSX 자체도 표현식입니다. babel과 같은 트랜스파일러에 의해 JSX는 일반적인 JS 함수 호출(`React.createElement()`)로 트랜스파일되며,  함수 호출의 결과인 JS 객체로 평가됩니다.

## 요약

- JSX는 React Element를 쉽게 생성하기 위해서 고안된 확장된 JS문법으로서, 실제 렌더링될 마크업과 데이터에 관한 로직을 컴포넌트내에서 동시에 작성할 수 있게 해줍니다.

### Further Step

- JSX로 인한 마크업 로직과 데이터 로직의 decoupling

## Reference

- [https://reactjs.org/docs/introducing-jsx.html](https://reactjs.org/docs/introducing-jsx.html)

- https://www.youtube.com/watch?v=LY6y3HbDVmg



VirtualDOM: 트리 구조를 나타내는 객체
