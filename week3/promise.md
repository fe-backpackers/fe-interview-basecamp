## 프로미스(Promise)란?

자바스크립트 비동기 처리에 사용되는 객체로, 비동기 작업의 동기적 표현을 가능하게 합니다. 

### 콜백 지옥(callback hell)

콜백 지옥은 콜백 함수를 익명 함수로 전달하는 과정이 반복되어 코드의 들여쓰기 수준이 감당하기 힘들 정도로 깊어지는 현상입니다. 주로 이벤트 처리나 서버 통신과 같이 비동기적 작업 수행을 위해 이런 패턴이 나타납니다. 

이러한 코드 구조는 가독성이 떨어지고 로직을 변경하기 어려운 문제가 있습니다. 또한 값이 아래에서 위로 전달되고 있어 어색함도 느껴집니다.

```jsx
setTimeout(function (name) {
	var coffeeList = name;
	console.log(coffeeList);

	setTimeout(function (name) {
		coffeeList += ', ' + name;
		console.log(coffeeList);

		setTimeout(function (name) {
			coffeeList += ', ' + name;
			console.log(coffeeList);

			setTimeout(function (name) {
				coffeeList += ', ' + name;
				console.log(coffeeList);
			}, 500, '카페라떼');
		}, 500, '카페모카');
	}, 500, '아메리카노');
}, 500, '에스프레소');
```

콜백 지옥을 해결하기 위해 익명의 콜백함수를 기명함수로 변환하는 방법이 있습니다. 

```jsx
var coffeeList = '';

var addEspresso = function (name) {
	coffeeList = name;
	console.log(coffeeList);
	setTimeout(addAmericano, 500, '아메리카노');
};
var addAmericano = function (name) {
	coffeeList += ', ' + name;
	console.log(coffeeList);
	setTimeout(addMocha, 500, '카페모카');
};
var addMocha = function (name) {
	coffeeList += ', ' + name;
	console.log(coffeeList);
	setTimeout(addLatte, 500, '카페라뗴');
};
var addLatte = function (name) {
	coffeeList += ', ' + name;
	console.log(coffeeList);
};
```

위와 같은 코딩 패턴으로 코드의 가독성을 높일 뿐 아니라, 위에서부터 아래로 순서대로 코드를 읽어내려갈 수 있습니다. 변수가 외부로 노출되었지만 즉시실행함수 등으로 감싸면 될 것입니다. 

하지만 외부로의 노출을 막는다 하더라도, 일회성 함수를 전부 변수에 할당해야 하는 단점이 있습니다. 

### 콜백 지옥(callback hell)을 해결하기 위한 프로미스(Promise)

프로미스는 위와 같은 비동기적인 작업을 동기적으로 보이게끔 해주는 장치로, ES6부터 도입된 객체입니다. 

프로미스를 이용해 위의 코드를 수정하면 다음과 같습니다. 

```jsx
new Promise(function (resolve){
	setTimeout(function () {
		var name = '에스프레소';
		console.log(name);
		resolve(name);
	}, 500);
}).then(function (prevName) {
	return new Promise(function (resolve) {
		setTimeout(function () {
			var name = prevName + ', 아메리카노';
			console.log(name);
			resolve(name);
		}, 500);
	};
}).then(function (prevName) {
	return new Promise(function (resolve) {
		setTimeout(function () {
			var name = prevName + ', 카페모카';
			console.log(name);
			resolve(name);
		}, 500);
	};
}).then(function (prevName) {
	return new Promise(function (resolve) {
		setTimeout(function () {
			var name = prevName + ', 카페라떼';
			console.log(name);
			resolve(name);
		}, 500);
	};
})
```

위의 코드를 보면 `new Promise()`, `resolve()`, `then()`과 같은 프로미스 API를 사용하는 것을 볼 수 있습니다. 이 API는 프로미스의 상태와 관련이 있습니다. 

### 프로미스의 세 가지 상태(states)

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/1ae43208-b593-494c-8c19-cc7c19b3baf0/Untitled.png)

- **pending**: 비동기 처리가 **fulfilled**되거나 **rejected**되지 않은 초기 상태. `new Promise()`로 프로미스를 생성하면 **pending** 상태를 갖습니다.
    
    ```jsx
    new Promise(function (resolve, reject){
    	/* 
    	 * 프로미스를 생성할 때 resolve 및 reject를 전달할 실행 함수를 넘겨줍니다. 
    	 * 실행함수는 모든 비동기 작업을 끝내면 resolve를 호출해 프로미스를 fulfilled하고,
    	 * 오류가 발생하면 reject를 호출해 거부합니다. 
    	 *
    	 *   resolve(someValue)       // fulfilled
    	 * or
    	 *   reject("failure reason") // rejected
    	 */
    });
    ```
    
- **fulfilled**: 연산이 성공적으로 완료된 상태. `resolve`를 호출하면 **fulfilled** 상태를 갖습니다. **fulfilled** 상태가 되면 `then()`을 이용해 **resolve**의 인수로 전달한 처리 결과 값을 받을 수 있습니다.
    
    ```jsx
    new Promise(function (resolve){
    	setTimeout(function () {
    		var name = '에스프레소';
    		console.log(name);
    		resolve(name);
    	}, 500);
    }).then(function (prevName) {
    		console.log(prevName); // '에스프레소'
    });
    ```
    
- **rejected**: 연산이 실패한 상태. `reject`를 호출하면 **rejected** 상태를 갖습니다. **rejected** 상태가 되면 실패 처리 결과 값을 `catch()`로 받을 수 있습니다.
    
    ```jsx
    function getEspresso(){
    	return new Promise(function(resolve, reject) {
    		reject(new Error("Request is failed"));
    	});
    }
    
    getEspresso().then().catch(function(err){
    	console.log(err); // Error: Request is failed
    });
    ```
    

## 정리

- 비동기 작업 처리시 발생하는 콜백 지옥을 해결하기 위해 ES6부터 **프로미스 객체**를 도입하였습니다.
- 프로미스는 비동기 작업을 동기적으로 보이게끔 하는 장치입니다.
- 프로미스는 `new Promise()`로 생성한 이후부터 pending, fulfilled, rejected 세 가지 상태를 갖습니다.

## 참고 자료

- 정재남, 『코어자바스크립트』, 위키북스(2019), p106-114.
- [https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/Promise](https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/Promise)
- [https://joshua1988.github.io/web-development/javascript/promise-for-beginners/](https://joshua1988.github.io/web-development/javascript/promise-for-beginners/)