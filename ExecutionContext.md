### 실행 컨텍스트란?

**실행 컨텍스트**는 자바스크립트 코드가 실행되고 연산되는 **범위**를 나타내는 추상적인 개념이다.

코어 자바스크립트(정재남, "코어 자바스크립트", 위키북스, 2019)에서는 다음과 같이 정의한다.

> 실행 컨텍스트란 실행할 코드에 제공할 환경 정보들을 모아놓은 객체이다.



코드가 실행되며 생성된 실행 컨텍스트는 호출 스택(Call Stack)에 쌓인다. 호출 스택은 실행 스택(Execution stack)이라고도 불린다.

자바스크립트 엔진이 `<script>` 태그를 처음 만나면 전역 (실행) 컨텍스트(Global Execution Context)가 생성되고 현재 실행 스택에 이를 push한다.

다른 함수가 push되었다면 실행 스택의 가장 꼭대기(top)에 있는 함수부터 실행하고, 실행이 완료한 함수는 스택에서 제거(pop)된다.

```jsx
var a = 1;
function outer(){
	function inner(){
		...
	}
	inner();
}
outer();
```

위 코드에서 실행 스택은 다음과 같다:

1. 전역 실행 컨텍스트 **push**
2. `outer()` 함수 실행 컨텍스트 **push**
3. `inner()` 함수 실행 컨텍스트 **push**
4. `inner()` 함수 실행 컨텍스트 **pop**
5. `outer()` 함수 실행 컨텍스트 **pop**
6. (모든 코드가 실행 완료되면) 전역 실행 컨텍스트 **pop**



대략적인 순서를 알았으니 좀 더 자세하게 살펴보자.

위에서 2, 3에서 일어나는 일은 다음과 같다.

- 전역 컨텍스트와 관련된 코드를 순차적으로 진행하다가 함수를 호출한다.
- 자바스크립트 엔진은 해당 함수에 대한 환경 정보를 수집해 해당 함수의 실행 컨텍스트를 생성한다.
- 생성된 함수 실행 컨텍스트를 콜 스택에 담는다.
- 콜 스택 꼭대기(top)에 새로운 함수 실행 컨텍스트가 놓였으므로, 실행 중인 전역 컨텍스트와 관련된 코드를 일시 중지하고, 새로운 함수 실행 컨텍스트와 관련된 코드를 실행한다.



실행 컨텍스트 객체는 활성화 되는 시점에 다음의 정보를 수집한다. 실행 컨텍스트 객체는 자바스크립트 엔진이 활용할 목적으로만 생성되므로, 개발자가 직접 확인할 수 없다:

- LexicalEnvironment

  ES6 공식 문서에 따르면, Lexical Environment(어휘적 환경)은 자바스크립트 코드의 어휘 중첩 구조를 기반으로 특정 변수(**let**, **const**)나 함수 식별자의 연결을 정의하는 타입이다.

  Environment Record와 외부 LexicalEnvironment의 레퍼런스로 구성되어 있다.

  - Environment Record는 Lexical Environment 내에서 생성된 식별자(컨텍스트를 구성하는 함수에 지정된 매개변수 식별자, 선언한 함수 및 변수 식별자 등) 바인딩을 기록한 정보이다. 
  ES6부터 this 바인딩을 Environment record에서 관리한다.
  - 외부 LexicalEnvironment로의 참조, 즉 외부 환경으로 접근 가능하다. 자바스크립트 엔진이 현재 lexical environment에서 변수를 찾지 못했다면 외부 환경에서 해당 변수를 찾아 볼 수 있다; scope chain.

  함수 실행 도중 변경사항이 실시간으로 반영된다.

  참고로, 전역 환경(Global environment)은 외부 환경을 가지지 않는(null) 어휘적 환경이다.

- VariableEnvironment

  현재 컨텍스트 내의 식별자(**var** 변수)들에 대한 정보. 선언 시점의 LexicalEnvironment의 스냅샷으로 **변경되지 않는다**.



### 정리

- **실행 컨텍스트**는 자바스크립트 코드가 실행되고 연산되는 **범위**를 나타내는 추상적인 개념이다.
- 자바스크립트 엔진이 `<script>` 태그를 처음 만나면 전역 (실행) 컨텍스트(Global Execution Context)가 생성되고 현재 실행 스택에 쌓인다. 함수 호출시마다 실행 컨텍스트가 생성되며 실행 스택에 쌓인다.
- 실행 컨텍스트 생성 후 함수가 실행된다. 이 때, 함수 내에서 사용되는 변수들은 먼저 변수 객체 안에서 값을 찾고, 없다면 scope chain을 통해 올라가며 찾는다.
- 실행 컨텍스트 객체는 활성화 되는 시점에 VariableEnvironment, LexicalEnvironment, ThisBinding 정보를 수집한다.
  - VariableEnvironment는 활성화 되는 시점에 담긴 현 컨택스트 내 식별자들에 대한 정보로, LexicalEnvironment의 스냅샷이다.
  - LexicalEnvironment는 함수 실행 도중 변경사항이 있다면 즉시 반영된다.
  - LexicalEnvironment는 Environment Record와 외부 LexicalEnvironment의 레퍼런스로 구성되어 있다.



### 참고 자료

https://262.ecma-international.org/6.0/#sec-executable-code-and-execution-contexts

https://blog.bitsrc.io/understanding-execution-context-and-execution-stack-in-javascript-1c9ea8642dd0