# VirtualDOM이란?

## 결론

- RealDOM을 추상화시킨 자바스크립트 객체이며, 메모리상에 존재합니다.

## 설명

- 돔 요소의 조작이 일어나면 돔트리 전체의 노드들이 처음부터 다시 렌더링 됩니다. 이 조작은 크리티컬 렌더링 패스로서 비용이 큰 연산이기 때문에 렌더링 성능이 저하됩니다.
- VirtualDOM을 사용하면 돔 요소의 조작이 일어날 때 실제 돔이 아닌, 리얼 돔과 구조가 같은 VirtualDOM 요소를 조작합니다. VirtualDOM은 상태가 이전과 다른 부분들만 한 번에 리얼돔에 반영합니다.
- 돔 요소의 조작이 일어날 때마다 돔트리 전체를 재 렌더링할 필요가 없어집니다.

## 요약

- VirtualDOM은 사용자에게 인터렉션에 따른 UI의 갱신을 효율적으로 제공하는 자바스크립트 객체입니다.

## 레퍼런스

- https://www.youtube.com/watch?v=PN_WmsgbQCo&t=441s
- https://velog.io/@bigsaigon333/Virtual-DOM
