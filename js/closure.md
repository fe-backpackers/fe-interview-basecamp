# Closure란?

## 결론

- 클로저는 함수가 선언되었을 때의 환경을 실행시에 참조하는 함수입니다.

## 설명

- JS에서 모든 함수는 자동적으로 함수가 선언된 `LexicalEnvironment`를 기억하고 있습니다.
- 함수가 실행되어 함수 본문에서 변수에 접근할 때, 현재 속한 실행 컨텍스트의 `LexicalEnvironment` 에서 변수를 찾아본 후, 변수가 존재하지 않으면 외부 `LexicalEnvironment` , 즉 함수가 선언된 `LexicalEnvironment`를 거슬러 가며 찾기 때문에, 함수가 선언된 환경을 실행시점에 참조할 수 있습니다.

## 요약

- 클로저는 선언된 곳의 외부 변수를 기억하고 이에 접근할 수 있는 함수로서, JS에서 모든 함수는 자연적으로 클로져입니다. (주1: 하나의 예외는 new Function syntax 입니다)

## Further Step

### Q. 어떻게 제거된 실행 컨텍스트 내에 존재하는 변수에 접근이 가능하죠?

- 일반적으로 함수 호출이 종료되면 활성화된 실행 컨텍스트의 `LexicalEnvironment`는 모든 변수와 함께 메모리에서 제거됩니다.
- 그러나 함수 호출이 종료된 후에도 여전히 해당 `LexicalEnvironment`에 도달 가능한 클로저가 존재한다면, 해당 `LexicalEnvironment` 는 GC의 대상에서 제외됩니다.

## Reference

- [https://javascript.info/closure#lexical-environment](https://javascript.info/closure#lexical-environment)
- [https://humorous-octagon-753.notion.site/b1fdfd69ce0e41dfb16bab7c570972b3](https://www.notion.so/b1fdfd69ce0e41dfb16bab7c570972b3)
- [https://meetup.toast.com/posts/118](https://meetup.toast.com/posts/118)
- [https://meetup.toast.com/posts/123](https://meetup.toast.com/posts/123)
- [https://velog.io/@bigsaigon333/closure-in-js](https://velog.io/@bigsaigon333/closure-in-js)
