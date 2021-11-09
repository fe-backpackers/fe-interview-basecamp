## 클로저(Closure)란?

클로저는 "함수가 선언할 때 참조한 외부 함수의 실행 컨텍스트가 종료된 이후에도 외부 lexical environment가 사라지지 않는 현상"입니다.

mdn에서는 클로저를 다음과 같이 정의하고 있습니다.

> A **closure** is the combination of a function bundled together (enclosed) with references to its surrounding state (the **lexical environment**). 
- [mdn](https://developer.mozilla.org/ko/docs/Web/JavaScript/Closures)
> 

여기서 함수를 둘러싸는 상태에 대한 참조, 즉 함수가 선언될 당시의 lexical envrionment는 실행 컨텍스트에서 `LexicalEnvironment`의 `outerEnvironmentReference`에 해당합니다. `outerEnvironmentReference`는 함수가 **선언될 당시**의 `LexicalEnvironment`에 대한 참조입니다. 

간단히 예제를 통해 `outerEnvironmentReference`를 알아보겠습니다.

```jsx
var a = 1;
var outer = function () {
	var inner = function () {
		console.log(a); 
		var a = 3;
	};
	inner();
};
outer();
console.log(a); 
```

여기서 함수 `inner`의 `outerEnvironmentReference`는 외부 함수 `outer`의 `LexicalEnvironment`에 대한 참조입니다.

그럼 도대체 **클로저**는 함수와 그 함수가 선언될 당시의 lexical environment(`outerEnvironmentReference`)가 어떻게 작용한 현상일까요? 

위의 예제를 조금 바꿔보겠습니다.

```jsx
var outer = function () {
	var a = 1;
	var inner = function () {
		return ++a;
	};
	return inner;
};
var outer2 = outer(); // f() { return ++a; }
console.log(outer2()); // 2
```

`outer`함수에서 `inner`함수 자체를 반환함으로써 이미 종료된 `outer`함수의 변수 `a`에 접근 가능해졌습니다. 

다시 말하면, `outer`함수가 반환한 `inner`함수는 `outer2` 변수에 담기고, `outer` 함수가 이미 종료된 시점에서 `inner`함수를 호출하여 `outer`함수 내부의 변수인 `a`에 접근하였습니다. 

즉, `inner`함수가 이미 종료된 `outer`함수의 `LexicalEnvironment`에 접근하였고, 그 결과 console에는 기존 `a`의 값에서 1이 증가된 2가 출력되는 것을 확인할 수 있습니다. 

이 현상이 바로 **클로저**입니다. 

### 클로저가 일어날 수 있는 이유

어떻게 이미 실행이 종료된 `outer`함수의`LexicalEnvironment`에 접근할 수 있는 것일까요? 바로 **가비지 컬렉터의 동작 방식** 때문입니다. 

카비지 컬렉터는 메모리 할당을 추적하고 할당된 메모리 블록이 더 이상 필요하지 않은지 판단하여 회수합니다. 즉, 개발자가 할당, 해제 여부를 결정하지 않고 가비지 컬렉터가 판단합니다. 

가비지 컬렉터의 판단 기준 중 하나는 다음과 같습니다: **어떤 다른 오브젝트도 참조하지 않는 오브젝트는 더 이상 필요하지 않은 오브젝트이다**. 

반대로 말하면 어떤 값을 참조하는 변수가 하나라도 있다면 가비지 수집 대상에 포함시키지 않습니다. 덕분에 클로저가 일어날 수 있는 것입니다. 

### 주의할 점

무조건 함수를 반환함으로써 외부로 전달할 수 있는 것은 아닙니다. 

```jsx
(function () {
	var a = 0;
	var intervalId = null;
	var inner = function () {
		if(++a >= 10){
			clearInterval(intervalId);
		}
		console.log(a);
	};
	intervalId = setInterval(inner, 1000);
})();
```

외부객체인 `window`의 메서드에 전달할 콜백 함수 `inner`내부에서 지역변수 `a`를 참조하고 있습니다. 이와 같이, 지역변수를 참조하는 내부함수를 외부에 전달하는 것도 클로저입니다. 

## 정리

- 클로저는 "함수가 선언할 때 참조한 외부 함수의 실행 컨텍스트가 종료된 이후에도 외부 lexical environment가 사라지지 않는 현상"입니다.
- 클로저는 `LexicalEnvironment`의 `outerEnvironmentReference`에서 외부 `LexicalEnvironment`를 참조하여 발생하는 현상입니다.
- 클로저는 어떤 오브젝트가 참조하고 있는 오브젝트는 가비지로 수집하지 않는 가비지 컬렉터의 동작 방식 때문에 발생하는 현상입니다.
- 함수를 반환하는 것 뿐만 아니라, 지역변수를 참조하는 내부함수를 외부에 전달하는 것도 클로저입니다.

## 참고 자료

- 정재남, 『코어자바스크립트』, 위키북스(2019), p115-122.
- [https://developer.mozilla.org/en-US/docs/Web/JavaScript/Closures](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Closures)
- [https://developer.mozilla.org/ko/docs/Web/JavaScript/Memory_Management](https://developer.mozilla.org/ko/docs/Web/JavaScript/Memory_Management)