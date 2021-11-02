# CORS란?

## 결론

- CORS란 JS를 이용하여 크로스 오리진 요청을 보낼 때, 서버가 응답 헤더를 통하여 명시적으로 허가한 크로스 오리진 요청만을 가능하게 하는 브라우저의 정책입니다.

## 설명

- 크로스 오리진 요청은 브라우저에서 본 요청이 이뤄지기 전에 preflight 요청을 보내 허가 여부를 물어봅니다.
  - 브라우저는 preflight 요청에 본 요청의 메서드 정보(`Access-Control-Request-Method`)와 본 요청의 헤더 정보(`Access-Control-Request-Headers` )를 담아서 보냅니다.
- 서버가 해당 크로스 오리진 요청을 허가하는 경우, preflight 요청에 대하여 상태 코드 200, 빈 본문으로 응답을 보냅니다.
  - 응답 헤더에는 허용되는 메서드 목록(`Access-Control-Allow-Methods`), 허용되는 헤더 목록(`Access-Control-Allow-Headers`), 몇 초간 preflight 요청 없이 크로스 오리진 요청을 바로 보낼지에 대한 정보(`Access-Control-Max-Age` )가 담겨있습니다.
- 브라우저는 preflight 응답이 성공한 경우에만 본 요청을 보냅니다.
- 다만, 메서드가 GET, POST, HEAD 이면서 정해진 헤더만을 가진 요청을 보통 안전한 요청이라고 부르며, 안전한 요청의 경우 preflight 요청 없이 바로 본 요청을 보냅니다.

## 요약

- CORS란 크로스 오리진 요청이 있을 때 브라우저가 어떤 오리진으로부터 리소스 로드를 허용하는지를 HTTP header를 통해 나타내는 메커니즘입니다.

## Further Step

- 오리진이란? 프로토콜, 도메인, 포트
- 안전한 요청의 구체적인 정의. (안전하지 않은 요청은 안전한 요청을 제외한 모든 요청이다)
  안전한 요청은 아래의 두가지 조건을 충족하는 요청입니다.
  1. 메서드가 GET 또는 POST
  2. 정해진 헤더만을 가지고 있음
    `Accept, Accept-Language, Content-Language, Content-type: application/x-www-form-urlencoded, multipart/form-data, text/plain`
- JS에서 안전하지 않은 헤더에 접근하기 위한 방법은?
- preflight 요청시에 cookie와 같은 credential 정보를 실어서 보내는 방법

## Reference

- [https://javascript.info/fetch-crossorigin](https://javascript.info/fetch-crossorigin)
- [https://developer.mozilla.org/en-US/docs/Web/HTTP/CORS](https://developer.mozilla.org/en-US/docs/Web/HTTP/CORS)
