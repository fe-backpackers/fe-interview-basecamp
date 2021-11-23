# 이벤트 루프란?

## 결론

- 이벤트 루프는 싱글 스레드 기반의 JS에서 비동기 연산을 가능하게 해주는 메커니즘입니다.

## 설명

- 이벤트 루프는 태스크가 들어오길 기다렸다가 테스크가 들어오면 이를 처리하고, 처리할 테스크가 없는 경우엔 잠드는, 끊임없이 돌아가는 루프입니다.

- JS 엔진은 비동기 연산의 실행을 브라우저에게 요청합니다. 브라우저는 비동기 연산이 완료되면 비동기 연산의 콜백 함수를 위한 새로운 태스크를 태스크 큐의 가장 마지막에 넣습니다.

- 이벤트 루프는 '현재 실행중인 태스크가 없을 때' 태스크 큐의 첫 번째 태스크를 꺼내와 실행합니다.
즉, 가장 오래된 태스크부터 순차적으로 처리합니다.

## 요약

- 이벤트 루프는 비동기 연산을 수행하기 위하여 실제 JS가 구동되는 환경과 JS 엔진이 상호 연동하기 위해 사용되는 메커니즘입니다.

## Further Step

- 호출 스택
- 마이크로 태스크 큐

## Reference

- https://velog.io/@bigsaigon333/%EC%9D%B4%EB%B2%A4%ED%8A%B8-%EB%A3%A8%ED%94%84-%EB%A7%88%EC%9D%B4%ED%81%AC%EB%A1%9C-%ED%83%9C%EC%8A%A4%ED%81%AC-%ED%81%90-in-JS
- https://youtu.be/cCOL7MC4Pl0
- https://jakearchibald.com/2015/tasks-microtasks-queues-and-schedules/
- https://developer.mozilla.org/en-US/docs/Web/JavaScript/EventLoop#event_loop
- https://meetup.toast.com/posts/89
