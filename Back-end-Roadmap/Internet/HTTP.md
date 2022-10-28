# HTTP란?

## 우선 클라이언트와 서버먼저 이해하기!
![img](https://velog.velcdn.com/images%2Frimu%2Fpost%2F6dc9dd95-955c-48c8-a933-fdd0e955eafb%2F%E1%84%89%E1%85%B3%E1%84%8F%E1%85%B3%E1%84%85%E1%85%B5%E1%86%AB%E1%84%89%E1%85%A3%E1%86%BA%202020-04-06%20%E1%84%8B%E1%85%A9%E1%84%8C%E1%85%A5%E1%86%AB%2011.31.58.png)
클라이언트란 요청(Request)을 보내는 쪽을 의미하며 일반적으로 WEB관점에서는 브라우저를 의미한다. 그리고 서버는 요청에 응답(Response)하는 쪽을 의미하며 일반적으로 데이터를 보내주는 컴퓨터를 의마한다. 이렇게 클라이언트와 서버가 상호작용하는 과정으로 웹이 이루어짐

## HTTP
HyperTexT Protocol의 약자이다. 문서를 전송하기 위한 약속을 뜻한다.

웹어서는 브랃우저와 서버 간에 데이터를 주고받기 위한 방식으로 HTTP 프로토콜을 사용하고있다.

## URL 의 구조
![img](https://velog.velcdn.com/images%2Frimu%2Fpost%2Ff2841c83-26b3-421e-bb93-3bd36d4aaa2b%2F%E1%84%89%E1%85%B3%E1%84%8F%E1%85%B3%E1%84%85%E1%85%B5%E1%86%AB%E1%84%89%E1%85%A3%E1%86%BA%202020-04-06%20%E1%84%8B%E1%85%A9%E1%84%8C%E1%85%A5%E1%86%AB%2011.50.15.png)
URL은 프로토콜 host port resource path query로 구성되어 있다.

## 클라이언트의 요청 HTTP Request요청 메서드
클라이언트가 서버에 데이터를 요청하는것은 식당에서 주문서를 작성하는것과 같다. 이 주문서는 서버가 클라이언트가 어떤걸 원하는지 파악할 수 있게 해준다. 여기서 요청하는 데이터에 특정 동작을 하도록 하기 위해서 바로 HTTP요청 메서드(HTTP Request Methods)을 이용한다.

일반적으로 HTTP 요청 메서드는 HTTP Verbs라고도 부르고 아래와 같은 메서드를 갖고 있다.

    GET: 존재하는 자원에 대한 요청
    POST: 새로운 자원을 생성
    PUT: 존재하는 자원에 대한 변경
    DELETE: 존재하는 자원에 대한 삭제

    (때에 따라서는 POST메서드로 PUT, DELETE동작도 가능하다)
 
 ## HTTP상태코드 
 HTTP 코드는 클라이언트의 요청에 대한 서버에서 설정해주는 응답 정보이다.
 ### 200번대 : 성공
    200:  GET요청에 대한 성공
    201: 정상적으로 생성이 되었다는걸 서버에서 알려줌(회원가입 등의 기능에서 사용한다.)
    204: No content. 성공했으나 응답 본문의 데이터가 없음
    205: Reset Content. 성공했으나 클라이언트의 화면을 새로 고침하도록 권고
    206: Partial Content. 성공했으나 일부 범위의 데이터만 변환
### 300번대 리다이레션
300번대의 상태 코드는 대부분 클라이언트가 이전 주소로 데이터를 요청하여 서버에서 새 URL로 리다이렉트르 유도하는 경우이다.

    301: Moved Permanently, 요청한 자원이 새 URL에 존재
    303: See other, 요청한 자원이 임시 주소에 존재
    304: Not Modified, 요청한 자원이 변경되지 않았으므로 클라이언트에서 캐시오딘 자원을 사용하도록 권고, ETag와 같은 정보를 활용하여 변경여부를 확인
### 400번대 클라이언트 에러
400번대 상태 코드는 대부분 클라이언트 코드가 잘못된 경우이다.

    400: Bad Request 잘못된 요청
    401: Unauthorized, 권한 없이 요청. Authorization 헤더가 잘못된 경우
    403: Forbidden, 서버에서 해당 자원에 대해 접근 금지
    404: Not Found, 요청한 자원이 서버에 존재하지 않음. 없는 url 또는 존재하지 않는 api를 가지고 요청했을때
    405: Method Not Allowed 허용되지 않는 메서드
    409: Conflict, 최신 자원이 아닌데 업데이트하는 경우
### 500번대: 서버 에러
    501: Not Implemented 요청한 대해 서버가 수행할 수 없는 경우
    503: Service Unaviable, 서버가 과부하 또는 유지 보수로 내려간경우