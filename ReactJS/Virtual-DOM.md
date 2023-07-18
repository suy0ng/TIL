# Virtual DOM

Virtual의 뜻 그대로 가상의 DOM이다.

### Virtual DOM의 동작

![img](https://velog.velcdn.com/images/tnrud4685/post/671735ed-20a9-4b58-9577-84dd64f12df6/image.png)

Virtual DOM을 사용하면 실제 DOM에 접근하며 조작하는 대신, 이를 추상화한 자바스크립트 객체를 구성하여 사용한다.
DOM의 상태를 메모리에 저장하고 변경 전과 변경 후의 상태를 비교한 뒤 최소한의 내용만 반영하기 때문에 성능 향상을 이끌어 낸다.
