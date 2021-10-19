# 원시타입

### 결론

자바스크립트의 타입으로, Number, String, Boolean, null, undefined, symbol, bigint가 있다. 불변값이다. 



### 설명

자바스크립트에는 원시타입과 객체타입이 있다.

원시타입으로는 Number, String, Boolean, null, undefined, symbol, bigint 7가지가 있으며, 불변값이다.

null과 undefined를 제외하고 모든 원시값은 래퍼객체가 있다.

따라서 new 연산자로 String 객체를 생성하지 않았더라도 sort와 같은 String 표준 내장 객체의 메서드를 사용할 수 있다. 

원시값이며 불변값으로 생성되었지만, 임시로 생성된 래퍼객체에서 메서드가 수행되기 때문이다. 



### 요약

Number, String, Boolean, null, undefined, symbol, bigint는 자바스크립트 원시타입이다. 



### 참고

https://developer.mozilla.org/ko/docs/Glossary/Primitive