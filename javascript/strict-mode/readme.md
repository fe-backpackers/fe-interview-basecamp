### strict mode란?

### 결론

기존에는 무시되던 **오류를 발생시킬 가능성이 높거나** 

**자바스크립트 엔진의 최적화 작업에 문제를 일으킬 수 있는 코드**에 대해 

**명시적인 에러**를 발생시킨다.



### 설명

사용법 : 전역의 선두 / 함수 몸체의 선두에 `'use strict';`를 추가한다.

효과 :  strict mode는 자바스크립트 언어의 문법을 보다 엄격히 적용한다. 

주의점 : 전역/함수 단위로 strict mode를 적용하는 것을 피하고, **즉시실행함수**로 감싼 **스크립트 단위**로 적용시키자.



### 요약

strict mode는 자바스크립트 코드에 더욱 엄격한 오류 검사를 적용한다.





### 참조

https://poiemaweb.com/js-strict-mode

https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Strict_mode

