## HTTP 메서드

클라이언트와 서버 사이에 이루어지는 요청과 응답 데이터를 전송하는 방식

</br>

### HTTP 메소드의 속성

1. 안전(Safe Methods)

   이 말은 계속해서 메소드를 호출해도 리소스를 변경하지 않는다는 뜻이다. 주요 메소드중에는 GET 메소드가 안전하다고 볼 수 있다.

2. 멱등(Idempotent Methods)

   이 말은 메소드를 계속 호출해도 결과가 똑같다는 뜻이다. GET, PUT, DELETE는 멱등하다고 볼 수 있지만 POST나 PATCH는 멱등하다고 볼 수 없다.

   PATCH가 왜 멱등하지 않다고 하는건지는 [여기](https://oen-blog.tistory.com/211)를 참고

3. 캐시가능(Cacheable Methods)

   캐시가능하다는 말은 말 그대로 캐싱을 해서 데이터를 효율적으로 가져올 수 있다는 뜻이다. GET, HEAD, POST, PATCH가 캐시가 가능하지만 실제로는 GET과 HEAD만 주로 캐싱이 쓰인다고 한다.

   </br>

### 멱등성(Idempotence)이란?

멱등성이란 여러번 수행해도 결과가 같음을 의미한다. 즉, 호출로 인하여 데이터가 변형이 되지 않는다는 것을 의미한다.

</br>

### HTTP 메서드는 총 9가지. 주요 메서드는 5가지.

주요 메서드

GET - 리소스 조회 (멱등성 o)

POST - 요청 데이터 처리, 주로 등록에 사용 (멱등성 x)

PUT - 리소스를 대체(덮어쓰기), 해당 리소스가 없으면 생성 (멱등성 o)

PATCH - 리소스 부분 변경 ( PUT은 전체 변경, PATCH는 일부 변경) (멱등성 x)

DELETE - 리소스 삭제 (멱등성 o)

</br>

기타 메서드

HEAD - GET과 동일하지만 메세지 부분(body 부분)을 제외하고, 상태 줄과 헤더만 반환

OPTIONS - 대상 리소스에 대한 통신 가능 옵션을 설명

CONNECT - 대상 자원으로 식별되는 서버에 대한 터널을 설정

TRACE - 대상 리소스에 대한 경로를 따라 메세지 루프백 테스트를 수행

</br>

### GET

리소스 조회 메서드

캐싱이 가능하여 같은 데이터를 한번 더 조회할 경우에 저장한 값을 사용하여 조회속도가 빨라짐

- 정적 데이터 조회 (이미지, 정적 텍스트 GET)

  쿼리 파라미터 없이 리소스 경로로 단순하게 조회 가능

  ex) GET /members/100

  1. 클라이언트에서 /members/100 으로 100번 멤버를 조회해서 정보를 달라고 GET 요청
  2. 서버에서는 요청 메세지를 분석해 내부의 멤버정보를 조회한 뒤 response를 만든다.
  3. 서버에서 클라이언트로 응답을 해줌. 클라이언트에서 정상적으로 받으면 200 OK status code를 받으며, 멤버정보를 얻게 됨.

- 동적 데이터 조회 (주로 검색, 게시판 목록에서 검색어로 이용)
  쿼리 파라미터 사용해서 데이터를 전달
  ex) GET /search?username=plla2&age=25
  1. 클라이언트에서 /search?username=plla2&age=25 으로 username이 plla2 이고 age가 25인 상세한 데이터를 조회해서 정보를 달라고 GET 요청
  2. 서버에서는 요청 메세지를 분석해 내부의 멤버정보를 조회한 뒤 response를 만든다.
  3. 서버에서 클라이언트로 응답을 해줌. 클라이언트에서 정상적으로 받으면 200 OK status code를 받으며, 멤버정보를 얻게 됨.

</br>

### POST

전달한 데이터 처리/생성 요청 메서드

메세지 바디를 통해 서버로 요청 데이터를 전달하면 서버는 요청 데이터를 처리하여 업데이트

ex) POST /members

{

“username”: ”plla”,

“age”: 25

}

1. 클라이언트는 body에 등록할 멤버 정보를 JSON 형태로 만들어 담고 서버로 전송
2. 서버에서는 받은 메세지를 분석해 로직대로 처리한다. (/members/100) 신규 리소스 식별자 생성
3. 신규회원에 대한 데이터를 바디에 담아서 클라이언트로 응답

</br>

### PUT

리소스를 대체(수정)하는 메서드

만일 요청 메세지에 리소스가 있으면 덮어쓰고, 없으면 새로 생성

> /members/번호 데이터가 존재하면 기존에 것을 완전 대체

> /members/번호 데이터가 없으면 새로 생성

ex) PUT /members/100

{

“username”: ”plla2”,

“age”: 50

}

1. 100번 멤버의 리소스를 교체하겠다는 요청 전송
2. 기존의 데이터가 있다면 완전히 대체
3. 만약 기존 데이터가 없었다면 POST와 같이 신규로 리소스를 생성

⭐️ 만약 age만 변경하고 싶다고

ex) PUT /members/100

{

“age”: 50

}

이런식으로 요청하면 100번 멤버의 리소스에서 username은 없어지고 age만 50으로 수정

</br>

### PATCH

리소스 일부 부분을 변경하는 메서드

PUT메서드에서 불가능했던 age만 50으로 변경하고싶을 때 사용

ex) PUT /members/100

{

“age”: 50

}

1. age만 50으로 변경하기 위해 해당 데이터를 PATCH로 전달
2. PUT과 다르게 100번 회원 정보에서 age만 변경

</br>

### DELETE

리소스를 제거하는 메서드

ex) DELETE /members/100

1. 100번째 멤버를 제거하기 위해 DELETE로 전달
2. 서버에서 요청을 받고 데이터베이스의 해당 리소스를 제거

</br>

### HTTP Method에 대한 질문

### POST방식이 GET방식보다 보안측면에서 더 좋다?

- GET과 비교하여 URL에 데이터의 정보가 들어 있지 않으므로 조금 더 안전하다고 볼 수 있다.

### GET방식이 POST방식보다 속도가 빠르다?

- GET 방식은 캐싱을 하기 때문에 여러번 요청시 저장된 데이터를 활용하므로 조금 더 빠를 수 있다.

### POST vs PUT

- POST와 PUT은 구분해서 사용해야한다. POST는 새로운 데이터를 계속 생성하기 때문에 요청시마다 데이터를 생성하지만, PUT은 사용자가 데이터를 지정하고 수정하는 것이기 때문에 같은 요청을 계속하더라도 데이터가 계속 생성되지는 않는다.

### PUT vs PATCH

- PATCH는 PUT이랑 조금 다름. PUT은 지정한 데이터를 전부 수정하는 Method이지만, PATCH는 정보의 일부분이 변경되는 방법입니다. 그래서 PUT은 멱등하지만, PATCH는 멱등하다고 볼 수 없습니다.

</br>
</br>
</br>

메서드 9가지를 다알고 싶다면 - [https://inpa.tistory.com/entry/WEB-🌐-HTTP-메서드-종류-통신-과정-💯-총정리](https://inpa.tistory.com/entry/WEB-%F0%9F%8C%90-HTTP-%EB%A9%94%EC%84%9C%EB%93%9C-%EC%A2%85%EB%A5%98-%ED%86%B5%EC%8B%A0-%EA%B3%BC%EC%A0%95-%F0%9F%92%AF-%EC%B4%9D%EC%A0%95%EB%A6%AC)

</br>

참고 - https://oen-blog.tistory.com/211