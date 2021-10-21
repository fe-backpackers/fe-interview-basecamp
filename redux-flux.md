## 리덕스에서 Flux란?

## 결론

리덕스는 Flux 패턴을 기반으로 만들어졌으며,
Flux 패턴은 단방향 데이터 흐름을 가진다는 특징을 가지고 있습니다.

## 설명

Flux패턴은 이전부터 존재하던 MVC, MVVM과 같은 M(Model)이 들어간 패턴들의 단점을 해결하기 위해 나왔습니다.
M이 들어가는 패턴들은 어플리케이션이 복잡해질수록 Model과 View간의 데이터 흐름의 로직이 복잡해진다는 단점이 있었습니다.

Flux패턴은 데이터 흐름을 Action -> Dispatch -> Store -> View 순으로 차례대로 데이터가 흐르게함으로써, View와 관련된 로직을 간소화할 수 있었고, 데이터의 흐름을 추적하기 쉬워진다는 장점이 있었습니다.

그리고 리덕스는 이 Flux 패턴을 기반으로 만들어졌고, 조금 변형하여 다음과 같은 구성요소를 가집니다.
Action, Action Creator, Reducer, Store, Dispatch

## 요약

리덕스의 Flux는 기존 MVC와 같은 Model과 연관된 패턴의 단점을 보완하기 위해나온 단방향 데이터흐름을 가지는 패턴입니다.

## 참고

https://www.huskyhoochu.com/flux-architecture/
