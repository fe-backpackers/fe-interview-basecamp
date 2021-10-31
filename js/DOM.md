## DOM Document Object Model

> HTML, XML 문서의 프로그래밍 인터페이스

HTML과 XML 문서의 구조를 정의하는 API를 제공합니다.  
구조화된 `node(element)`, `property`, `object`로 문서를 표현할 수 있습니다.    
문서 내 element 간의 부자관계를 반영하여 모든 element들을 tree 구조로 구성할 수 있습니다.   
그리고 우리는 element를 정의하고 각각의 element에 접근하는 방법(프로퍼티, 메소드)을 제공합니다.  
→ 문서 구조, 스타일, 내용 등을 변경할 수 있게 도와줍니다.

예를 들면,

``` html
<!DOCTYPE html>
<html>
    <head>
        <title>제목</title>
    </head>
    <body>
        <h1 id="header"> Hello, Challenger!</h1>
        <div id="content">
        
        </div>
    </body>
</html>
```
이런 식으로 html 문서가 있는 경우, 우리는 DOM을 이용하여 문서 내용을 수정할 수 있습니다.
``` javascript
const $content = document.querySelector("#content"); // id가 content인 element를 선택합니다. (element 접근)

const $div = document.createElement("div");          // div type의 element 정의
$div.appendChild(document.createTextNode("Bye~"));   // 'Bye~'라는 textNode를 생성(element 접근)하여 $div의 자식 element로 설정
$content.appendChild($div);                          // $content의 자식 element로 $div 추가
```


이렇게 DOM 은 웹 페이지를 스크립트 또는 프로그래밍 언어들에서 사용될 수 있게 _연결_ 해주는 역할을 합니다.


<br/>

> API (web or XML page) = DOM + JS (scripting language)  
 