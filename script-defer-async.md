## `<script>, <script async>, <script defer>` 차이는?

## 결론

설명에 앞서 script가 js파일을 다운로드 받을때에는 다음과 같은 요소들을 고려할 수 있습니다.

script를 다운받고 script를 실행하는 것이 html을 파싱하는것을 블로킹 하느냐에 따라서 설명할 수 있습니다.

## 설명

script 태그만 사용하는 것은 script 다운로드와 script 실행이 html 파싱을 모두 블로킹합니다.

script async를 사용하면,
script 다운로드는 html 파싱과 병렬적으로 이루어집니다.
하지만 script 실행은 html 파싱을 블로킹합니다.
(+다운로드가 끝난시점에서 바로 script가 실행됩)

script defer는 script 다운로드가 html 파싱과 병렬적으로 다운로드 되면서 html파싱이 모두 끝난뒤에 script가 실행되어 html파싱을 블로킹하지 않습니다.

## 요약

\_ `<script/>` : script 다운로드, 실행 모두 블로킹.

- `<script async/>`: script 다운로드는 병렬, 실행은 블로킹, script 다운로드가 끝나자마자 실행이됨

- `<script defer/>` : script 다운로드 병렬, script 실행은 html파싱이 끝나고 수행됨
