## 결론

<br>

JSX는 자바스크립트에 XML 문법을 추가해 쉽게 리액트 엘리먼트를 표현하도록 확장한 문법이다.

<br>

## 설명

<br>

### 1. XML이란?
- eXtensible Markup Language
- HTML과 유사하게 태그 문법을 사용
- HTML의 목적이 정보를 화면에 어떻게 표현할지 미리 정의된 태그로 나타내는 것이라면 XML의 목적은 태그 이름을 통해 데이터를 그룹화하고 구조화 하는 것이다.
- 예시
  ```xml
  <애플>
    <스마트폰>아이폰</스마트폰>
    <태블릿>아이패드</태블릿>
    <노트북>맥북</노트북>
  </애플>
  <삼섬>
    <스마트폰>갤럭시</스마트폰>
    <태블릿>갤럭시탭</태블릿>
    <노트북>갤럭시북</노트북>
  </삼섬>
  ```

<br>

### 2. JS를 어떻게 확장할까?
- JSX에서는 태그를 통해 리액트 엘리먼트를 나타낸다.
- JSX 파서는 태그 안의 정보를 이용해 React.createElement를 호출한다.
  - 태그의 첫 단어는 type인자로, 태그로 감싼 부분은 children으로 그 외 나머지는 props인자로 취급된다.
    ```jsx
    <elementType prop1="prop1" prop2="prop2">
      some text
    </type>

    // 위 태그는 아래 표현과 동일하다.

    React.createElement(elementType, { prop1: "prop1", prop2: "prop2" }, "some text");
    ```
- 이때, 각 태그는 XML 문법이기에 사용자가 임의로 정의해 사용할 수 있다. 단, 기존 HTML 태그도 함께 지원한다. 이를 동시에 지원하는 방법은 다음과 같다.
  - 태그의 첫 단어가 소문자로 시작한다면 이는 문자열로 해석된다.
  - 태그의 첫 단어가 대문자로 시작한다면 이는 식별자로 해석된다.
    ```jsx
    <div /> 
    // parse
    React.createElement("div");  

    const Span = "span"
    <Span>
    // parse
    React.createElement(Span);
    // Span === "span"이므로
    React.createElement("span");
    ```
- 위와 같은 성질을 이용해 기존 html 태그를 사용할때는 소문자, 사용자 정의 컴포넌트를 사용할 때는 대문자를 사용한다.

<br>

## 요약

<br>
 - JSX는 자바스크립트에 XML 문법을 추가해 확장한 문법이다.
 - JSX에서 태그는 리액트 엘리먼트를 나타낸다.
 - JSX에서는 주로 html 태그를 나타낼때 소문자, 컴포넌트를 나타낼 때 대문자로 시작하는 태그이름을 사용한다.