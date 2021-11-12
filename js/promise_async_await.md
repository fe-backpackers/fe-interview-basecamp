
## Promise
ES6에 추가된 JS 내장객체  
> new Promise(executor)   

promise를 생성할 때, `executor`라는 매개변수를 받는다.  
`executor`는 매개변수로 두 가지 함수를 받는다. →  `resolve`, `reject`    
* `resolve`: 비동기를 성공적으로 완료한 결과를 값으로 받아낼 때 호출된다.    
* `reject`: 작업 실패하여 오류의 원인을 받아낼 때 호출된다.  

내부에서 `resolve`, `reject` 호출하기 전에는 `then`, `catch` 구문으로 넘어가지 않는다.  
→  `resolve`, `reject`를 통해 비동기의 작업의 동기적인 표현을 가능하게 해준다.


## Async/Await
ES2017에서 추가된 `promise`의 syntatic sugar  
class문법을 통해 자바스크립트의 프로토타입을 쉽게 사용할 수 있듯이 `async/await`를 통해 `promise`를 좀 더 쉽게 사용할 수 있다.  

## async
`new Promise`를 통해 promise 객체를 생성하지 않더라도 자동적으로 함수 안의 코드 블럭들이 `promise`로 변환된다.  
``` javascript
const challenge = async() => {
    return '챌린지';
};
```

## await  
wait!! 하는 역할  
함수 앞에 `async`를 명시해줘야 한다.  
비동기 로직이 실행되는 동안 함수의 실행을 멈추고 반환을 기다린다.  
``` javascript 
const timeout = (ms) => {
    return new Promise((resolve) => setTimeout(resolve, ms));
};

const print = async () => {
    console.log('hello');
    await delay(1000);
    console.log('world');
};

print(); // hello 찍힌 후 1초 뒤 world가 찍힌다. 

```
`await` 덕분에 비동기(async) 코드로 작성했지만 동기(sync) 코드 처럼 위에서 아래로 순차적으로 읽는게 가능해졌다.  
→ **가독성 좋아짐 !**   

때로는 `async/await` 쓰는 거 보단 `promise` 쓰는 게 나을 수도 있다.  
콜백함수 작성하다가 지옥 같이 느껴진다면 `promise`와 `async/await`을 쓰도록 하자!  


<br/><br/>

[참고](https://www.youtube.com/watch?v=wvEYG6ydAGg)


