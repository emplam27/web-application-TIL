# jQuery & Ajax



## jQuery란?

HTML 요소들을 조작하는 편리한 JavaScript 라이브러리

- JavaScript와 다른 특별한 소프트웨어가 아니라 미리 작성된 코드를 모아둔 것

- 직접 JS 코드를 작성하여 모든 기능을 구현할 수도 있지만, 이 경우에 코드가 복잡하고, 개발환경과 다른 브라우저에서 잘 작동을 안하는 등 브라우저 간 호환성을 직접 고려해야하는 등의 문제가 있기 때문에 전문 개발자가 작성한 라이브러리를 가져와서 사용하면 편함.

- **대신, 쓰기 전에 import 필수**

- JQuery와 순수 JavaScript의 코드를 비교해보면,

  JS에서 `elememt`란 id를 가진 요소를 감추려면

  ```jsx
  document.getElementById("element").style.display = "none";
  ```

  이렇게 길고 복잡하게 써야하지만, JQ로는

  ```jsx
  $('#element').hide();
  ```

  이렇게 간단하고 직관적으로 쓸 수 있음





## jQuery 사용하기

- jQuery를 사용하기 위해서는 미리 작성된 JavaScript 코드를 CDN으로 임포트

  ```html
  <script src="<https://ajax.googleapis.com/ajax/libs/jquery/3.4.1/jquery.min.js>"></script>
  ```

- jQuery를 사용하는 방법

  CSS와 마찬가지로 jQuery를 쓸 때 특정 요소를 '가리켜야' 조작할 수 있습니다. CSS에서는 선택자로 class를 주로 사용했는데, jQuery에서는 고유한 하나의 요소를 가리키는 id를 주로 사용합니다.







## 자주 쓰이는 jQuery



#### (1) input 박스의 값 가져오기

- html

   ```html
   <div class="form-group">
       <label for="exampleInputEmail1">아티클 URL</label>
       <input id="post-url" type="email" class="form-control" aria-describedby="emailHelp"
           placeholder="">
   </div>
   ```

- js

  ```js
  // input의 값 가져오기
  let url = $('#post-url').val()
  
  // input에 값 넣기
  $('#post-url').val("새 글입니다.")
  ```



#### (2) div 숨기기 / 보이기

- html

  ```html
  <div class="posting-box" id="post-box">
      ...
  </div>
  ```

- js

  ```js
  // id 값이 post-box인 곳을 가리키고, hide()로 안보이게 한다.(=css의 display 값을 none으로 바꾼다)
  $('#post-box').hide();
  
  // show()로 보이게 한다.(=css의 display 값을 block으로 바꾼다)
  $('#post-box').show();
  ```




#### (3) CSS의 속성 값 가져오기

- js

  ```js
  // CSS의 display 속성이 변하는 것 확인 가능
  $('#post-box').hide();
  $('#post-box').css('display');
  
  $('#post-box').show();
  $('#post-box').css('display');
  ```





#### (4) 태그 내 텍스트 입력하기

- html
    ```jsx
    <button id="btn-posting-box" type="button" class="btn btn-primary">포스팅박스 열기</button>
    ```

- js

   ```jsx
   let btn_text = $('#btn-posting-box').text(); 
   btn_text         // '포스팅박스 열기'가 출력
   $('#btn-posting-box').text('포스팅박스 닫기');
   ```



#### (5) 태그 내 html 입력하기

- html

  ```html
  <div id="cards-box" class="card-columns">
      <div class="card"> ... </div>
  </div>
  ```

- js

  ```js
  let img_url = 'https://cdn.vox-cdn.com/thumbor/Pkmq1nm3skO0-j693JTMd7RL0Zk=/0x0:2012x1341/1200x800/filters:focal(0x0:2012x1341)/cdn.vox-cdn.com/uploads/chorus_image/image/47070706/google2.0.0.jpg';
  let link_url = 'https://google.com/';
  let title = '제목 - 구글';
  let desc = '구글에 대한 설명이 여기에 들어간다.';
  let comment = '여기는 개인적인 코멘트가 들어간다.';
  
  let temp_html = `<div class="card">
                      <img class="card-img-top"
                          src="${img_url}"
                          alt="Card image cap">
                      <div class="card-body">
                          <a href="${link_url}" class="card-title">${title}</a>
                          <p class="card-text">${desc}</p>
                          <p class="card-text comment">${comment}</p>
                      </div>
                  </div>`;
  $('#cards-box').append(temp_html);
  ```





#### (6) 페이지 로딩이 완료되면 실행하기

- js

  ```html
  <script>
  
  $(document).ready(function(){
  	alert('페이지가 로딩되었습니다.')
  });
  
  </script>
  ```

  



## Ajax



#### CDN import

```html
<script src="https://ajax.googleapis.com/ajax/libs/jquery/3.4.1/jquery.min.js"></script>
```



#### 기본골격

```js
$.ajax({
  type: "METHOD",
  url: "",
  data: {},
  success: function(response){
    console.log(response)
    // 로직 구현
  }
})
```

