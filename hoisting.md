## 호이스팅(hoisting)이란?

실행 컨텍스트가 활성화되는 시점에 선언된 변수가 위로 끌어올려지는 것을 말한다.

실행 컨텍스트에 대해 이해하고 있다는 가정 하에 글을 작성하였습니다.

컨텍스트 내부 전체를 처음부터 끝까지 순서대로 훑으며 환경 정보에 대한 수집을 마치면, 코드가 실행되기 전임에도 불구하고 자바스크립트 엔진은 해당 환경에 속한 코드의 변수명에 대한 정보를 모두 알고 있게 된다.

이는 마치 식별자들이 최상단으로 끌어올려진 것(hoist)과 같다고 하여 **호이스팅(hoisting)**이라고 부른다.


## 호이스팅 규칙

**변수는 선언부와 할당부를 나누어 선언부만 끌어올리는 반면, 함수 선언은 함수 전체를 끌어올린다.**

```jsx
console.log(b); // f b(){}
var b = 'bbb';
console.log(b); // 'bbb'
function b(){};
```

위 코드는 아래와 같이 볼 수 있다.

```jsx
var b;
b = function b(){};
console.log(b); // f b(){}
b = 'bbb';
console.log(b); // 'bbb'
```

위의 예시와 같이, 변수 b는 선언부인 `var b;`만 끌어올려졌지만, 함수선언문 함수 전체를 끌어올려진 것(`var b = function b(){}`)을 확인할 수 있다.

**주의할 점은 함수 선언문(function declaration)과 함수 표현식(function expression)의 차이이다.** 함수 선언문은 함수 선언문은 함수 전체가 끌어올려지지만, 함수 표현식은 정의한 function을 별도의 변수에 할당하는 것이므로 변수 선언부만 끌어올려진다.

```jsx
console.log(sum(1, 2)); // 3
console.log(multiply(1, 2)); // Uncaught TypeError: multiply is not a function

function sum(a, b){
    return a + b;
}

var multiply = function(a, b){
    return a * b;
}
var sum = function sum(a, b){
    return a + b;
}
var multiply;
console.log(sum(1, 2));
console.log(multiply(1, 2));

multiply = function(a, b){
    return a * b;
}
```

**`var`와 `let`, `const`의 호이스팅은 다르다.** `var`는 function-level scope로 변수를 선언하기 이전에 참조할 수 있지만, `let`, `const`는 block-level scope로 변수를 선언하기 이전에 참조할 수 없다.

```jsx
console.log(x); // undefined
console.log(y); // Uncaught ReferenceError: y is not defined
var x = 2;
const y = 1;
```

이는 `var`은 선언과 동시에 초기화되지만, `let`, `const`는 선언과 초기화가 분리되어 진행되기 때문이다.

- `var`은 스코프에 변수를 등록(선언)하고, 메모리에 변수를 위한 공간을 확보한 후, undefined로 값을 초기화한다.

- `let`, `const`는 스코프에 변수를 등록(선언) 후, 변수 선언문에 도달했을 때 초기화가 이루어진다. 초기화 이전에 변수에 접근하려고 하면 참조에러(ReferenceError)가 발생한다.

  참고로, 스코프의 시작 지점부터 초기화 시작 지점까지 변수를 참조할 수 없기 때문에 이 구간을 Temporal Dead Zone(TDZ)라고 부른다.


## 정리

- 호이스팅(hoisting)이란 실행 컨텍스트가 활성화되는 시점에 선언된 변수가 위로 끌어올려지는 것을 말한다.
- 변수는 선언부와 할당부를 나누어 선언부만 끌어올리는 반면, 함수 선언은 함수 전체를 끌어올린다.
- 함수 선언문은 함수 선언문은 함수 전체가 끌어올려지지만, 함수 표현식은 정의한 function을 별도의 변수에 할당하는 것이므로 변수 선언부만 끌어올려진다.
- `var`는 변수를 선언하기 이전에 참조할 수 있지만, `let`, `const`는 변수를 선언하기 이전에 참조할 수 없다.


## 참고자료

https://developer.mozilla.org/ko/docs/Glossary/Hoisting

https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Statements/let#시간상_사각지대

https://262.ecma-international.org/5.1/#sec-10.5

https://stackoverflow.com/questions/28246589/order-of-hoisting-in-javascript 