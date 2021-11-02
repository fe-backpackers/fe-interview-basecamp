## 결론

<br>

virtualDOM은 가상화된 DOM이자 UI의 변화를 관리하는 기능이다.

<br>

## 설명

<br>

### 1. virtualDOM은 가상화 된 DOM이다.
  - DOM은 엘리면트로 구성된 트리이다. 따라서 virtualDOM은 가상화된 엘리먼트로 구성된 트리이다.
  - 이는 virtualDOM을 구현하기 위해 먼저 가상 엘리먼트가 정의되어야하고 이 엘리먼트가 어떤 방식에 의해 만들어지는지 정의되어야 한다.(createElement)
### 2. virtaulDOM을 실제 DOM에 반영하기 위해 렌더러가 구현되어야한다.
### 3. virtualDOM의 동작
  - 사용자는 가상화 된 엘리먼트 트리(virtualDOM)을 만들어 렌더러에 전달한다.
  - 최초 렌더시에는 virtualDOM의 내용을 실제 DOM으로 변환하여 그대로 반영한다.
    - 이때, virtualDOM은 메모리에 저장된다.
  - 기존에 저장되어 있는 virtualDOM이 있다면 렌더러는 새로운 virtualDOM과 기존의 virtualDOM을 비교하여 변경된 부분만을 실제 DOM에 반영한다.
  - 기존의 virtualDOM을 새로운 virtualDOM으로 대체한다.

<br>

## 요약

<br>

- virtualDOM은 가상화된 DOM이다.
- virtualDOM은 비교를 통해 변화를 DOM에 반영한다.
- virtualDOM의 사용자는 상태에 따른 UI의 모습(가상화된 엘리먼트)을 렌더러에 전달하는 일만 한다.

<br>

## 추가

<br> 

- virtualDOM과 유사한 IncrementalDOM도 있다. 
- incrementalDOM은 가상화된 돔이 아닌 실제 돔을 이용해 UI 변경점을 찾는 방식이다.