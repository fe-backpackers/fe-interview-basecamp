#자바스크립트에서 this란?

## 결론

- this는 자신이 속한 객체 또는 자신이 생성할 인스턴스를 가리키는 자기 참조 변수이다.
- 단, this가 가리키는 값, 즉 this 바인딩은 함수가 호출되는 방식에 따라 동적으로 결정된다. 또한 strict mode 역시 this 바인딩에 영향을 준다.
(바인딩이란 식별자와 값을 연결하는 과정. 예로 변수 선언은 변수 이름(식별자)와 확보된 메모리 공간의 주소를 바인딩 하는 것이다. )

## 설명

자바스크립트는 스크립트 언어로, 인터프리터에 의해 줄 단위로 읽혀서 해석되어 실행됩니다.
인터프리터에 의해 현재 실행되는 자바스크립트의 환경을 실행 컨텍스트라고 합니다. 자바스크립트 내부에서 이러한 실행 컨택스트를 스택으로 관리하며, 실행되는 시점에 자주 변경되는 실행 컨택스트를 this가 가리킵니다.

즉, this는 현재 실행되는 코드의 실행 컨텍스트를 가리킵니다.

- 1. 일반 함수 내부에서 this는 전역 객체(Global Object)와 바인딩됩니다. 즉 브라우저에서는 window 객체입니다. 
<pre>
<code>
this
< Window {0: global, ...

function a(){console.log(this);};
a();
< Window {0: global, ...
</code>
</pre>
   단, strict mode일 경우에는 undefined입니다.

- 2. 메서드 내부에서 this는 메서드를 호출한 객체와 바인딩됩니다.

<pre>
<code>
let player = {
  name : "player1",
  method(){
    console.log(`${this.name} uses a gun.`)
  }
}
player.method();//'player1 uses a gun'
</code>
</pre>

this는 player가 됩니다.
이것은 객체의 메서드를 호출할 때 this를 내부적으로 바꿔주기 때문입니다. 

참고) ``은 백틱이라 하며 javascript에서 백틱(`)을 사용하여 문자열을 표현하는 것을 템플릿 리터럴이라고 한다.
  \n을 사용하지 않고 줄바꿈을 쉽게 할 수 있으며, 문자열 내부에 표현식을 포함 할 수 있고, 표현식을 사용함으로써 ("")('')(+)등의 문자열을 포함하기 위해서 사용했던 것을 사용하지 않아도 되어 번거로움을 덜 수 있다.

- 3. 생성자 함수 내부에서 this는 생성자 함수가 생성할 인스턴스와 바인딩됩니다. 

<pre>
<code>
function Player(name, age){
  this.name = name,
  this.age = age;
};
Player.prototype.method=function(){
  console.log(this.name,this.age);
}

var police = new Player('police', 29);
police.method();//police 29

</code>
</pre>

주의) new를 사용하여 호출한 경우에만 해당됩니다. 

- 4. Call, Apply, Bind 메서드 사용시, this는 메서드에 첫 번째 인수로 전달되는 객체에 바인딩됩니다.

Call 메서드는 함수를 실행하고, 첫 번째 인자에 this를 바인딩하며, 이후의 값을 함수의 인자로 전달합니다.
Apply 메서드는 함수를 실행하고, 첫 번째 인자에 this를 바인딩하며, 이후의 값을 배열의 형태로 받아 차례로 함수의 인자로 전달합니다. bind 메서드는 함수를 실행하지 않으며, 첫 번째 인자에 this를 바인딩한 새로운 함수를 반환한다. 

- 5. 위의 규칙 중 다수가 적용되면 더 상위 규칙이 승리합니다. 

- 6. 함수가 ES2015 화살표 함수일 경우, 위의 모든 규칙을 무시하고 생성된 시점에서 주변 스코프의 this값을 받습니다. 

## 요약

javascript에서 this는 함수가 호출되는 방식에 따라 다르게 결정되며 일반 함수일 경우, 메서드 내부일 경우, new를 사용하여 생성자 함수를 사용할 경우, call,Apply,Bind 메서드를 사용할 경우 다릅니다.

## Further Stemp

- 실행 컨텍스트
- 프로토타입, 프로토타입 상속
- new 연산자, 생성자
- call, apply, bind 메서드

## Reference

-[https://velog.io/@realryankim/JavaScript-this%EB%9E%80](https://velog.io/@realryankim/JavaScript-this%EB%9E%80)   
-[https://www.zerocho.com/category/JavaScript/post/5b0645cc7e3e36001bf676eb](https://www.zerocho.com/category/JavaScript/post/5b0645cc7e3e36001bf676eb)
-[http://frontendinterviewhandbook.com/kr/javascript-questions/](http://frontendinterviewhandbook.com/kr/javascript-questions/)   
-[https://velog.io/@danmin20/%EC%9E%90%EB%B0%94%EC%8A%A4%ED%81%AC%EB%A6%BD%ED%8A%B8-this-%EB%B0%94%EC%9D%B8%EB%94%A9%EC%9D%B4%EB%9E%80](https://velog.io/@danmin20/%EC%9E%90%EB%B0%94%EC%8A%A4%ED%81%AC%EB%A6%BD%ED%8A%B8-this-%EB%B0%94%EC%9D%B8%EB%94%A9%EC%9D%B4%EB%9E%80)   
-[https://stonefree.tistory.com/68](https://stonefree.tistory.com/68)(백틱)   
-모던 자바스크립트 Deep Dive
