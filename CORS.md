# CORS란?

## 결론

- CORS란 보안 상의 이유로 타 도메인과의 통신을 차단하는 SOP(Same-Origin-Policy)라는 정책을 HTTP 헤더를 이용한 인증을 통해 리소스로의 접근에 대한 권한을 부여하는 것입니다.

## 설명

### 등장 배경

- 인증 토큰 등과 같은 중요한 정보가 브라우저의 쿠키에 저장됩니다.
- 쿠키는 XSS 공격을 통해서 탈취할 수 있기 때문에 사용자 정보가 유출될 우려가 있습니다.
- 브라우저는 동일한 도메인과의 통신만 허용하여 이러한 보안 공격을 예방하였습니다.
- 브라우저가 동일한 도메인과의 통신만을 허용하는 정책을 `Same-Origin-Policy`라고 합니다.
- 이후, 웹의 규모가 커지면서 다른 출처의 리소스를 가져오는 등의 통신이 필요해졌습니다.
- 그래서 개발자들은 JSONP 등의 방식을 통해서 우회하여 타 도메인과 통신을 하는 방법을 사용했습니다.
- 이후, 어떤 조건을 충족하는 도메인이라면 출처가 다른 도메인이라도 통신을 허용하도록 하는 메커니즘인 CORS라는 것이 등장하였습니다.

### 동작 원리

- 브라우저는 서버로 요청을 보낼 때 `Origin`이라는 HTTP 헤더에 요청하는 쪽의 URL을 담아서 서버로 전달합니다.
- 요청을 받는 서버 측에서는 응답을 돌려줄 때 `Access-Control-Allow-Origin` HTTP 헤더에 요청을 허용하는 URL을 담아서 보내줍니다.
- 브라우저는 서버에서 받은 응답의 `Access-Control-Allow-Origin`에 해당 URL이 있는지 확인하고 있다면 통신을 허용합니다.

### 메소드별 통신 과정

- 메소드에 따라 두 가지 방식으로 통신을 합니다.
- GET, POST, HEAD 등의 메소드는 Simple Request라고 하며, 이외의 PUT, DELETE 등의 메소드는 Preflight Request라고 합니다.

1. Simple Request

- Simple Request는 Access-Control-Allow-Origin 헤더를 이용한 방법으로 통신하는데, 사용자의 인증 정보를 다루는 통신의 경우에는 추가적인 조치를 해야합니다.
- 통신을 보내는 쪽에서는 XMLHttpRequest 혹은 fetch API에 withCredentials 옵션을 설정하고 요청을 전송합니다.
- 서버에서는 인증 정보를 확인하고 정상적인 인증 정보인 경우에만 돌려줄 응답의 `Access-Controll-Allow-Credentials` HTTP 헤더를 true로 설정하여 응답을 돌려줍니다.
- 만약 `Access-Controll-Allow-Credentials`가 true가 아니라면 브라우저에서 해당 통신을 차단하게 됩니다.

2. Preflight Request

- PUT, DELETE 메소드의 통신은 사용자 데이터를 변경하는 메소드이기 때문에 본격적인 통신을 하기 전에 OPTIONS 메소드를 통해서 안전 여부를 사전에 확인합니다.
- 이렇게 OPTIONS메소드를 미리 전송한다고 해서 Preflight Request라고 합니다.
- OPTIONS는 본 요청의 메소드는 어떤 것이고, HTTP 헤더에는 어떤 것이 포함될지를 서버에 미리 알려줍니다.
- 서버가 해당 메소드와 헤더를 허용하는지를 확인하고 허용하는 경우에만 본 통신이 이루어집니다.

## 요약

- CORS는 다른 출처와 자원을 공유하는 경우에 특정 조건을 만족하는 도메인과의 통신을 허용하도록 하는 메커니즘입니다.
- 메소드 별로 동작 과정에 차이가 있으며, 사용자 인증에 관련된 통신의 경우에는 추가적인 HTTP 헤더 설정과 XMLHttpRequest/fetch API에 대한 추가 옵션 설정이 필요합니다.
- 사용자 데이터에 변경을 가하는지의 여부에 따라 단순 요청과 사전 요청으로 분류합니다.

## 참고자료

1. [velog pilyeooong - CORS란 무엇인가?](https://velog.io/@pilyeooong/CORS%EB%9E%80-%EB%AC%B4%EC%97%87%EC%9D%B8%EA%B0%80)
2. [얄팍한 코딩사전 웹개발 짜증 유발자 CORS](https://www.youtube.com/watch?v=bW31xiNB8Nc)
3. [MDN - CORS](https://developer.mozilla.org/ko/docs/Web/HTTP/CORS)
4. [MDN - OPTIONS Method](https://developer.mozilla.org/en-US/docs/Web/HTTP/Methods/OPTIONS)
