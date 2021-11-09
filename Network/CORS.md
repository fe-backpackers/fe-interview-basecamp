# CORS란?

## 결론

- 교차 출처 리소스 공유(Cross-Origin Resource Sharing)로 현재 웹 애플리케이션에서 다른 웹 애플리케이션의 리소스에 접근할 수 있는 권한을 브라우저에서 판단하는 체제입니다.

## 설명

- SOP(Same origin Policy)는 다른 웹 애플리케이션에서 리소스를 사용하지 못하게 제한하여 보안을 유지합니다.
- CORS는 다른 웹 애플리케이션의 리소스에 접근할 경우 HTTP 헤더를 사용하여 권한을 검증합니다.
- 권한을 검증하는 방법은 3가지로 단순 요청(Simple Request), 프리플라이트 요청(Preflight Request), 인증정보 포함 요청(Credentialed Request)이 있습니다.

## 요약

- CORS의 체제에서는 다른 웹 애플리케이션에 접근하여 리소스를 이용할 수 있으므로 서비스를 좀 더 마이크로서비스로 개발할 수 있습니다.

## 레퍼런스

- https://www.youtube.com/watch?v=-2TgkKYmJt4
- https://www.youtube.com/watch?v=7iGIfcEsc2g
- https://www.youtube.com/watch?v=_sLjXviYivM
