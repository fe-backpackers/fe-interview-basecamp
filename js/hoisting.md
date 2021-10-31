## 호이스팅 Hoisting
영어 그대로 해석하자면 끌어 올리기라는 의미를 갖고 있다.  
스코프 안에서만 변수 선언만 된다면 변수 조회 시 오류가 나지 않는다.  
아무데나 변수 선언만 하면 최상단에서 변수 선언한 것과 동일한 역할을 한다고 생각하면 된다.

```
console.log(str2); // undefined
var str2='hello';
console.log(str2); // hello
```
오류가 나지 않는다!  
<br/>

* let의 hoisting
```
console.log(str3);
let str3='hello';
console.log(str3);
```
> Uncaught ReferenceError: str3 is not defined

* const의 hoisting
```
console.log(str4);
const str4='hello';
console.log(str4);
```
> Uncaught ReferenceError: str4 is not defined

let과 const는 변수 hoisting이 되지 않는 게 아니라,  
**변수 초기화(메모리 공간 확보하고 undefined로 초기화) 되지 않았기 때문에** _(일시적 사각지대(Temporal Dead Zone; TDZ))_  
변수 선언하는 코드 이전에서는 변수를 참조할 수 없기 때문이다.

