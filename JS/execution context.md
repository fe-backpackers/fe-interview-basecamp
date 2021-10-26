# 실행 컨텍스트

- 결론
    - 실행컨텍스트는 식별자(변수, 함수, 클래스 등의 이름)를 등록하고 관리하는 스코프와 코드 실행 순서 관리를 구현한 내부 메커니즘으로, 모든 코드는 실행 컨텍스트를 통해 실행되고 관리됨
- 설명
    - 4가지 타입의 소스코드는 실행 컨텍스트를 생성(전역, 지역, eval, 모듈)
    - 식별자, 스코프 : 렉시컬 환경으로 관리
    - 코드 실행 순서 : 실행 컨텍스트 스택으로 관리
    - 실행 컨텍스트 구조
    
    ![Untitled](https://media.vlpt.us/images/jiseong/post/f9173745-1fd6-4315-ac8e-7bc788130e4c/image.png)
    
    실행 컨텍스트 구조 (출처: [https://velog.io/@jiseong/%EC%8B%A4%ED%96%89-%EC%BB%A8%ED%85%8D%EC%8A%A4%ED%8A%B8-Execution-Context](https://velog.io/@jiseong/%EC%8B%A4%ED%96%89-%EC%BB%A8%ED%85%8D%EC%8A%A4%ED%8A%B8-Execution-Context))
    
- 요약
    - 실행 컨텍스트는 소스코드를 실행하는데 필요한 환경을 제공하고 코드의 실행 결과를 관리하는 영역
- 참조
    - 모던 자바스크립트 Deep Dive
    - https://velog.io/@jiseong/%EC%8B%A4%ED%96%89-%EC%BB%A8%ED%85%8D%EC%8A%A4%ED%8A%B8-Execution-Context
