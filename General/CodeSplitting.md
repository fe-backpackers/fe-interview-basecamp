# 웹팩의 코드 스플리팅이란?

## 결론

- 지금 당장 필요하지 않은 코드는 따로 분리시켜 필요할 때 불러와 사용합니다.

## 설명

- 웹팩은 기본적으로 자원을 미리 로딩하지 않고 필요할 때 요청하여 성능을 높이고자 합니다.
- 바벨의 stage-3 단계에 있는 dynamic import 문법을 자동 지원하고 있으므로 import 함수를 사용하여 로딩이 필요할 때 코드를 불러올 수 있습니다.
- 모듈을 비동기적으로 CommonJS 형태로 불러와 사용합니다.

## 요약

- 나중에 필요한 자원은 나중에 로딩하는 레이지 로딩을 가능하게 하여 페이지 로딩 속도를 높입니다.

## 레퍼런스

- https://joshua1988.github.io/webpack-guide/motivation/why-webpack.html#%ED%8C%8C%EC%9D%BC-%EB%8B%A8%EC%9C%84%EC%9D%98-%EC%9E%90%EB%B0%94%EC%8A%A4%ED%81%AC%EB%A6%BD%ED%8A%B8-%EB%AA%A8%EB%93%88-%EA%B4%80%EB%A6%AC
- https://zereight.tistory.com/969
- https://velog.io/@velopert/react-code-splitting
