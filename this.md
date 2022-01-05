
# this와 this 바인딩

## 결론
this는 자바스크립트 실행 컨텍스트가 생성을 위한, 실행되기 위한 조건 중 한가지 요소이고, this의 바인딩은 자바스크립트 런타임 때 어떻게 호출했느냐에 따라서 정해진다.

## 설명
this를 어떻게 호출했느냐에 따라서 this가 가리키는 객체는 달라집니다.
4가지 케이스를 크게 두고 볼 수 있습니다.

- 1번째 케이스 - 일반함수로 호출하였을 때 

  일반 함수로 호출 시 this는 항상 전역 객체 (browser js - window | node.js - global)
  를 가리킵니다.

  <pre>
  <code>
      var a = 10; // window.a = 10
      
      function fn(){
        console.log(this.a); // window.a
      }
      
      fn();
  </code>
  </pre>

- 2번째 케이스 - 객체의 메서드로 this 바인딩 시 
  
  객체의 메서드의 내부에 this를 호출 시 this는 메서드를 감싸는 객체를 가리킵니다.

  <pre>
  <code>
      var a = 10;
      
      function fn(){
        console.log(this.a);
      }
      
      var obj = { a : 20, fn : fn };
      
      fn(); // 10
      obj.fn(); // 20
  </code>
  </pre>
  
  주의 할 점은 메서드 내부에서 함수를 호출 시 해당 함수의 this는 전역 객체를 바인딩합니다. 이는 1번 케이스에서 설명한 바와 같이 함수로써 호출했기 때문입니다.

  두번 째로 주의 할 점은 화살표 함수는 정적 this바인딩을 수행하기 때문에 화살표 함수로 만든 메서드 내부에서 this를 사용하지 않더라도, 화살표 함수로 메서드를 만드는 법은 가급적이면 피하고 ES5에서 부터 나온 새로운 [단축구문](https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Functions/Method_definitions "MDN link") 또는 function 을 사용하도록 권장되어있습니다.

- 3번째 케이스 - 콜백 함수로 호출 시

  콜백함수의 this는 일반적으로는 전역객체를 바라보지만, call, apply, bind의 메서드를 사용하게되면 this를 원하는 객체로 바인딩이 가능합니다.

  <pre>
  <code>
    var a = 10;
    var obj = { a : 20 };
    
    function fn(callback,obj){
      return callback.call(obj);
    }
    
    function callback(){
      return this.a;
    }
    
    console.log(fn(callback, null)); // 10
    console.log(fn(callback, obj)); // 20
</code>
</pre>

- 4번째 케이스 - new 연산자로 새로운 객체 생성시
  
  new로 새로운 객체 생성시 this는 새로운 객체를 가리키게 됩니다.
  
  <pre>
  <code>
    function Human(name, age){
      this.name = name;
      this.age = age;
    }
    
    var human = new Human('Minsu', 25);
    console.log(human.name, human.age) // Minsu, 25
  </code>
  </pre>

  new 연산자로 Human의 새로운 인스턴스를 받는 과정에서 Human 함수내에 암시적으로 새로운 객체가 생성되고, this에는 새로 생성된 객체가 바인딩 된 후 실행하게 됩니다.

## 결론
this는 함수, 메서드를 어떻게 호출했느냐에 따라서 this의 바인딩 객체가 달라진 것을 확인 할 수 있었습니다.

일반함수로 호출하면 전역객체를, 메서드로써 호출하면 메서드를 감싸는 객체에 대해서, 콜백으로 호출하면 일반적으로는 전역, call, apply, bind메서드를 사용시에는 임의의 객체를 this로 바인딩 시키고, new 연산자로 호출하게 되면 호출한 함수(객체)를 this로 바인딩 시키게 됩니다.

---

 \+ 추가 내용 - 엄격모드의 this 바인딩

코드 에디터의 맨 첫번째 줄에 "use strict"(엄격모드)를 사용하게 되면 this의 전역객체 바인딩이 허용되지않고, 전역객체를 바인딩하게 되는 this들에게 undefined를 선사합니다.

때문에 엄격모드에서 this를 사용시 undefined 오류에 주의해야합니다.

--- 
참고한 문서, 블로그

정재남 개발자님의 코어 자바스크립트 강의.

MDN this : https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Functions

PoiemWeb 함수 호출 방식에 의해 결정되는 this : https://poiemaweb.com/js-this