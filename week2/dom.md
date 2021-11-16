# DOM(Document Object Model)

**DOM(Document Object Model)**은 웹 문서를 브라우저가 이해할 수 있는 구조로 구성하여 메모리에 적재한 것으로, DOM API를 통해 웹 문서를 동적 변경할 수 있다. 



### DOM Tree

DOM은 웹 문서의 구조화된 표현을 제공하는데 트리 구조로 이루어져있다. 

```html
<html>
  <body>
    <p>
      Hello World
    </p>
    <div>
      <img src="example.png" />
    </div>
  </body>
</html>
```

예를 들어, 위와 같은 html 문서를 파싱하여 다음과 같이 객체의 트리로 구조화되있는 **DOM 트리**로 구축할 수 있다.  

<img src="https://d2.naver.com/content/images/2015/06/helloworld-59361-8.png" alt="domtree" style="zoom:75%;" />



즉, DOM은 텍스트 파일로 구성된 웹 문서를 브라우저에 렌더링하기 위해선 브라우저가 이해할 수 있는 트리구조로 메모리에 적재한 것이다. 



## 정리

* DOM(Document Object Model)은 HTML, XML 문서의 프로그래밍 인터페이스다.
* DOM은 문서의 구조화된 표현을 제공하며, 프로그래밍 언어는 DOM API를 통해 DOM 구조에 접근하고 웹 문서를 동적 변경할 수 있다. 



## 참고자료

https://developer.mozilla.org/ko/docs/Web/API/Document_Object_Model/Introduction

https://poiemaweb.com/js-dom

https://d2.naver.com/helloworld/59361

