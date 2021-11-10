# VirtualDOM

## 결론

- Real DOM과 동일한 구조를 가지지만, 메모리상에 존재하는 자바스크립트 객체입니다.

## 설명

- 실제 DOM 요소를 조작하는 것은 매우 비용이 큰 연산(**크리티컬 렌더링 패스**)이므로, DOM 요소의 조작이 여러번 반복되는 경우에는 렌더링 성능이 저하될 수 있습니다.
- VDOM을 사용하여 실제 DOM요소를 조작하지 않고 VDOM요소를 조작한 후, VDOM 이전과 이후 상태를 비교(**Reconciliation**)하여 변경된 부분만을 단 한번 실제 DOM에 반영함으로써 효율적으로 DOM요소를 렌더링할 수 있습니다.

## 요약

- Virtual DOM이란 UI의 갱신을 효율적으로 수행하기 위하여 실제DOM의 구조를 띄며 메모리상에서 동작하는 객체입니다.

### Further Step

- V-DOM의 특징: light, immutable, stateless
- 크리티컬 랜더링 패스
- Reconciliation

## Reference

- [https://www.youtube.com/watch?v=PN_WmsgbQCo&t=441](https://www.youtube.com/watch?v=PN_WmsgbQCo&t=441)
- [https://reactjs.org/docs/faq-internals.html#gatsby-focus-wrapper](https://reactjs.org/docs/faq-internals.html#gatsby-focus-wrapper)
- [https://velog.io/@sbinha/React에서-Virtual-DOM](https://velog.io/@sbinha/React%EC%97%90%EC%84%9C-Virtual-DOM)
- [https://jeong-pro.tistory.com/210](https://jeong-pro.tistory.com/210)
- [DOM은 뭐고 가상 DOM은 뭔가요? (+ Svelte와 React의 차이)](https://www.youtube.com/watch?v=1ojA5mLWts8)
