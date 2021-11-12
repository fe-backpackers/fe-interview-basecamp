

### ajax (asynchronous javascript and xml)
서버와 비동기적으로 데이터 주고 받는 js 기술로 ajax를 이용하여 페이지 전체가 아닌 일부만 수정할 수 있습니다.

과거에는 웹 서버에서 html 파일을 받아와 화면을 렌더링했습니다.  
이와 같은 방식은 브라우저가 전부 새로고침되어 새로 렌더링되기 때문에 비효율적입니다.

ajax를 이용하면 화면 새로고침없이 필요한 부분만 새로 렌더링할 수 있습니다.  
웹페이지 전환이 부드러워져 사용자 만족도 뿐만 아니라 성능도 좋아집니다.  
하지만 클라이언트 렌더링 방식으로 검색엔진 최적화(Search Engine Optimization, SEO) 이슈가 있습니다.  


---

- async/await + ajax
``` javascript
async function callFunc() {
    let response = await fetch(url주소);
    if(!response.ok) {
        throw new Error('error');
    }
    let result = await response.json();
    console.log(result);
}
callFunc().catch(()=> {
    console.log('error');
});
```

- jquery를 이용하여 ajax를 사용할 수 있습니다.
``` javascript
$.ajax({
    url: url주소,
    type: 'get',      // 서버로 요청하는 방식
    dataType: 'json', // 서버가 보내주는 데이터 타입
    success: function(result) {
        console.log(result);
    },
    error: function() {
        console.log('error');
    }
    
});
```

- react나 vue에서는 axios 라는 외부라이브러리를 사용하여 ajax를 쓸 수 있습니다.
``` javascript
axios.get(url주소)
    .then((result) => {
        console.log(result);
    }).catch(() => {
        console.log('error');
    });
```