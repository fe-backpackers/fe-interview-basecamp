# Flux란?

## 결론

- Flux는 웹 앱의 데이터 흐름을 관리하기 위한 패턴으로서, 데이터가 한 방향으로만 흐르기 때문에 상태의 변경이 예측가능하다는 장점이 있습니다.

## 설명

<p align="center">
  <img width="700" src="https://user-images.githubusercontent.com/31029000/137587886-26c594e6-f463-4a77-9b4c-144cdd6e90fd.png" />
</p>

- Flux Architecture의 주요 요소로는 View, Dispatcher, Store가 있으며, 데이터는 항상 View → Dispatcher → Store → View 의 단방향으로만 흐릅니다.
- 유저와의 인터랙션이 있어 상태를 변경해야 하는 경우, View는 Action을 생성하여 Dispatcher에게 전송합니다.
- View로부터 Action 을 전달받은 Dispatcher는 Store(s)에 Action을 전달합니다.
- Action을 전달받은 Store는 상태를 갱신하며, 상태 갱신 후 View에게 상태가 변경되었다는 사실을 알려줍니다.
- 이와 같이 View가 직접 Store 내의 상태를 변경하지 않기 때문에 상태 변경의 복잡성이 줄어들고 상태 변경을 예측가능하게 해줍니다.

## 요약

- Flux Architecture는 데이터를 한 방향으로만 흐르게 하여 상태 변경을 예측가능하게 해주는 구조입니다.

## Further Step

- Redux에서 Flux Architecture란?

## Reference

- [https://facebook.github.io/flux/docs/in-depth-overview](https://facebook.github.io/flux/docs/in-depth-overview)
- [https://facebook.github.io/flux/docs/dispatcher/](https://facebook.github.io/flux/docs/dispatcher/)
- [https://beomy.tistory.com/44](https://beomy.tistory.com/44)
