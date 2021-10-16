# CORS란?

## 결론

- CORS란 JS를 이용하여 크로스 오리진 요청을 보낼때 서버로부터 명시적으로 크로스 오리진 요청을 '허가'했다는 것을 알려주는 헤더를 전송받았을 때만 크로스 오리진 요청을 가능하게 하는 브라우저의 정책입니다.

## 설명

- 크로스 오리진 요청에는 안전한 요청과 안전하지 않은 요청, 두가지 종류가 있습니다.
- **안전한 요청**의 경우 Origin 헤더와 함께 바로 요청이 전송되며, 서버는 해당 크로스 오리진 요청을 허용하는 경우, Header의 `Access-Control-Allow-Origin` 에 해당 Origin 값을 포함시켜 응답합니다.
- **안전하지 않은 요청**은 브라우저에서 본 요청이 이뤄지기 전에 preflight 요청이라 불리는 사전 요청을 보내 허가 여부를 물어봅니다.
    - 브라우저는 preflight 요청에 본 요청의 메서드 정보(`Access-Control-Request-Method`)와 본 요청의 헤더 정보(`Access-Control-Request-Headers` )를 담아서 보냅니다.
    - 서버가 해당 크로스 오리진 요청을 허용하는 경우, preflight 요청에 대하여 상태 코드 200, 빈 본문으로 응답을 보냅니다. Response Header에는 허용되는 메서드 목록(`Access-Control-Allow-Methods` ), 허용되는 헤더 목록(`Access-Control-Allow-Headers` ), 몇 초간 preflight 요청 없이 크로스 오리진 요청을 바로 보낼지에 대한 정보(`Access-Control-Max-Age` )가 담겨있습니다.
    - 브라우저는 preflight 응답이 성공한 경우에만 본 요청을 보냅니다.

## 요약

- CORS란 크로스 오리진 요청이 있을 때 브라우저가 어떤 오리진으로부터 리소스 로드를 허용하는지를 HTTP header를 통해 나타내는 메커니즘입니다.

## Further Step

- 오리진이란? 프로토콜, 도메인, 포트
- 안전한 요청의 구체적인 정의. (안전하지 않은 요청은 안전한 요청을 제외한 모든 요청이다)
- JS에서 안전하지 않은 헤더에 접근하기 위한 방법은?

## Reference

- [https://javascript.info/fetch-crossorigin](https://javascript.info/fetch-crossorigin)
- [https://developer.mozilla.org/en-US/docs/Web/HTTP/CORS](https://developer.mozilla.org/en-US/docs/Web/HTTP/CORS)
