
## CDN (Content Delivery Network)
컨텐츠를 전송해주는 네트워크로, 온라인의 모든 곳에서 빠르고 안정적이며 일관된 경험(컨텐츠)을 제공해준다.  

- 원활한 웹 컨텐츠 제공
- 대용량 미디어도 안전하게 전송 가능  
- 트래픽이 줄어듬으로써 서버 유지 비용도 감소

👉 origin 서버에 직접 도달할 필요 없이, CDN 네트워크에 있는 서버에 접속해 해당 컨텐츠를 받을 수 있다.  
 


---

#### 

``` html
<script src="https://cdn.jsdelivr.net/npm/vue/dist/vue.js"></script>


<script crossorigin src="https://unpkg.com/react@17/umd/react.development.js"></script>
<script crossorigin src="https://unpkg.com/react-dom@17/umd/react-dom.development.js"></script>
```
개발하다보면, 위와 같이 직접 다운로드 받을 필요없이 cdn을 이용하여 라이브러리를 사용하는 경우가 있다.  
해당 코드가 실행되는 시점에서 CDN에 접근하여 필요한 정보를 실시간으로 다운받아 사용하게 된다.  
네트워크 통신을 사용하기 때문에 (느리다고 느껴지지는 않지만)느리고, 네트워크에 연결이 안 된 경우 작동하지 않는다.  

CDN을 사용함으로써 매우 쉽고 가볍게 개발할 수 있다. 

