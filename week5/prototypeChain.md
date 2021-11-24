자바스크립트는 프로토타입 기반 언어라 불립니다. 이는 모든 객체들이 메소드와 속성들을 상속 받기 위한 템플릿으로써 **프로토타입 객체(prototype object)**를 가진다는 의미입니다. 

프로토타입 객체도 상위 프로토타입 객체로부터 메소드와 속성을 상속 받을 수 있고, 그 상위 프로토타입 객체 역시 마찬가지입니다. 이를 **프로토타입 체인(prototype chain)**이라 부릅니다. 


### 프로토타입 객체와 프로토타입 체인

생성자 함수를 정의하고 그에 대한 인스턴스를 만들어봅시다.

```jsx
function Person(first, last, age, gender) {
	this.first = first;
	this.last = last;
	this.age = age;
	this.gender = gender;
}

const person1 = new Person('Jordan', 'Choi', 26, 'female');
```

Person의 인스턴스인 person1을 생성한 후 콘솔에 "person1."을 치면 해당 객체의 멤버이름을 자동 완성 팝업으로 보여줄 것입니다. 해당 팝업창을 확인해보면 `person1`의 프로토타입 객체인 `Person()`에 정의된 멤버 뿐 아니라 `Person()`의 프로토타입 객체인 `Object`에 정의된 다른 멤버도 볼 수 있습니다. 

![Prototype Chain(출처: [MDN](https://developer.mozilla.org/ko/docs/Learn/JavaScript/Objects/Object_prototypes))](https://mdn.mozillademos.org/files/13891/MDN-Graphics-person-person-object-2.png)


어떤 생성자 함수를 new 연산자와 함께 호출하면, 생성자에서 정의된 내용을 바탕으로 새로운 인스턴스(`person1`)를 생성합니다. 이 때 instance에는 `**__proto__`라는 속성이 자동으로 부여되는데, 이 속성은 생성자의 `prototype`이라는 프로퍼티를 참조**합니다.  

`__proto__`라는 속성을 사용하여 프로토타입에 접근하는 것은 자바스크립트 표준에서 권장되는 방식이 **아닙니다**. 
ES5.1에는 `__proto__`가 아닌 `[[prototype]]`이라는 명칭으로 정의되어있으며, 이는 private 속성으로 프로토타입이 되는 다른 객체를 가리킵니다. 즉 `__proto__`는 `[[prototype]]`을 구현한 대상일 뿐으로 표준에서는 `__proto__`에 직접 접근하는 것을 허용하지 않습니다. 오직 `Object.getPrototypeOf(obj)` 메소드로만 접근 가능합니다.
다만, 대부분의 브라우저에서 `__proto__`에 직접 접근하는 것을 허용하고 있기 때문에 레거시 코드에 대한 호환성을 고려하여 ES6부터 정식으로 인정하고 있지만 **권장되는 방식은 아닙니다**. 

이로 인해 `person1`에서 `Object`에 정의되어있는 메소도인 `valueOf()`를 호출할 수 있습니다. person1 인스턴스에서는 숨겨진 속성인 `[[prototype]]`를 통해 프로토타입 객체의 메소드에 접근할 수 있게 되기 때문입니다. 

 이 과정을 풀어 설명하겠습니다. 

1. 브라우저는 `person1`객체가 `valueOf()` 메소드를 가지고 있는지 체크합니다. 
2. 없다면 `person1`의 프로토타입 객체인 `Person()` 생성자의 프로토타입에 `valueOf()` 메소드를 가지고 있는지 체크합니다. 
3. 또 없다면 `Person()` 생성자의 프로토타입 객체의 프로토타입 객체 (`Object()` 생성자의 프로토타입)가 `valueOf()` 메소드를 가지고 있는지 체크합니다. 
4. Boom! 발견하였으니 호출하며 끝납니다. 만약 발견하지 못했다면 `undefined`가 됩니다.

위의 과정처럼 어떤 메소드나 속성을 호출했을 때 없다면 자신의 프로토타입 내에서 찾고, 또 없다면 프로토타입의 프로토타입에서 찾아가는 과정을 **프로토타입 체이닝**이라고 합니다. 그리고 우리는 이 프로토타입 체이닝을 통해 각 프로토타입 메소드를 자신의 것처럼 호출할 수 있습니다. 자신으로부터 가장 가까운 대상부터 검색하며, 원하는 값을 찾으면 검색을 중단합니다. 


### 정리

- 모든 객체는 메소드와 속성을 상속받는 **프로토타입 객체(prototype object)**를 가진다.
- 객체의 프로토타입(`Object.getPrototypeOf(obj)`)과 생성자의 `prototype` 속성은 같다.
    
    ```jsx
    const foo = new Foo();
    Object.getPrototypeOf(foo) === Foo.prototype; // true
    ```
    
- 프로토타입 객체도 상위 프로토타입 객체로부터 메소드와 속성을 상속 받을 수 있고, 그 상위 프로토타입 객체 역시 마찬가지다. 즉, 어떤 메소드나 속성을 호출했을 때 없다면 자신의 프로토타입 내에서 찾고, 또 없다면 프로토타입의 프로토타입에서 찾으며, 이 과정을 **프로토타입 체이닝(prototype chaining)**이라고 한다.


### 참고자료

- [https://developer.mozilla.org/ko/docs/Learn/JavaScript/Objects/Object_prototypes](https://developer.mozilla.org/ko/docs/Learn/JavaScript/Objects/Object_prototypes)
- 정재남, 『코어자바스크립트』, 위키북스(2019), p146-174.